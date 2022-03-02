# Redis 란?

- Redis is an open source in-memory data structure store, used as a database, cahce and message broker.

- Cache is a temporary storage component area where the data is stored so that in future, Data can be served faster

- 레디스(Redis)는 고성능 key-value 저장소로서 리스트, 해시, 셋 정렬된 셋 등 여러 형식의 자료구조를 지원하는 NoSQL입니다.

- Redis holds its database entirely in the memory, using the disk only for persistence
- Redis는 데이터를 disk에 저장할 수 있습니다. 따라서 Redis는 서버가 shutdown된 후에 restart 하더라도 disk에 저장해놓은 데이터를 다시 읽어서 데이터가 유실되지 않습니다.

- Redis is written in ANSI C.
  - C언어로 작성되어 Java와 같이 가상머신 위에서 동작하는 언어에서 발생하는 성능 문제에 대해 자유롭습니다. 곧바로 기계어로 동작하지 않고 어떤 가상의 머신 위에서 인터프리터된 언어로 가동하는 경우에는 가비지컬렉션(Garbage Collection) 동작에 따른 성능 문제가 발생할 수 밖에 없습니다. 하지만 C언어로 작성된 Redis는 이런 이슈에 대해 자유롭습니다.

## 다운로드

- https://redis.io/download

```sh
cd Downloads/redis-version(설치한 버전)/src
sudo make install  // building our C files 이것을 하려면 Xcode를 설치해야함 mac에선 이명령어를 실행하면 자동으로 Xcode를 설치합니다.
```

## Working with Keys in Redis

- set key value [EX secons|PX milliseconds|KEEPTTL] [NX|XX]

  - ex) set 1 "hello"
  - 같은 키에 새로운 value 를 설정하면 overwritten 됩니다.

- get key

  - ex) get 1

- del key [key ...]

  - ex) del 1

- exists key [key ...]

- set expire // seconds단위 설정

  1. set a "hello" ex 20 // 20초뒤에 a라는 키는 삭제 됩니다.

  - ttl a // ttl명령어는 a라는 키가 몇초뒤에 삭제되는지 보여줍니다.
    - ttl key 명렁어 이후 결과가 -2가 나오면 key 가 존재하지 않는 것이고 존재하지만 expire 명령어가 없는 key이면 -1이 나옵니다.

  2. expire key seconds

  - ex. expire a 20

  3. persist key

  - expire도중 취소시키고 싶으면 이 명령어를 사용합니다.

- set expire // milliseconds단위 설정
  1. set a "hello" Px 100 // 20초뒤에 a라는 키는 삭제 됩니다.
  - pttl a // pttl명령어는 a라는 키가 몇초뒤에 삭제되는지 보여줍니다.
    - pttl key 명렁어 이후 결과가 -2가 나오면 key 가 존재하지 않는 것이고 존재하지만 expire 명령어가 없는 key이면 -1이 나옵니다.
  2. pexpire key milliseconds
  - ex. pexpire a 200000
  - ttl 은 초단위로 바꿔주고 pttl 밀리 초 단위뢰 확인 가능하다.
  3. persist key
  - expire도중 취소시키고 싶으면 이 명령어를 사용합니다.

## Pattern Matchi

> h?llo matches hello, hallo and hxllo
> h\*llo matches hllo and heeeello
> h[ae]llo matches hello and hallo, but not hillo
> h[^e]llo matches hallo,hbllo, but not hello
> h[a-b]llo matches hallo and hbllo

- keys pattern // pattern을 가진 key들을 보여줍니다.
  - ex. keys h?llo

## Understanding shutdown command

redis-server // server start
redis-cli // client is connected to the server

ping // 입력후 Pong 이 뜬다면 client가 server에 연결 성공했다는 뜻

shutdonw nosave // 서버 다운 client 1 이 서버를 다운하면 모든 클라이언트의 연결이 끊긴다.

shutdonw save // save옵션을 추가하면 서버의 연결이 끊겨도 disk에 정보가 기록이 됩니다.

## Some more commands

```sh
Randomkey  // 저장된 키들 중 랜덤으로 하나를 나타냅니다

Rename key newkey // 키의 이름을 수정합니다.

renamenx key newkey // newkey가 존재하면 rename이 적용되지 않습니다.

touch key // 마지막 접근시각을 현재 시각으로 변경합니다.

unlink key // del과 같이 키를 삭제하지만 asynchronously 형식으로 삭제합니다.

type key // key에 저장되있는 value가 어떤 type인지 알려줍니다.

dump key // 백업의 의미 , dump한 것은 redis의 버전이 다르면 사용할 수 없습니다. 실행 시에 serial key가 제공이되는데 이 key를 복사를합니다.

restore key // dump를 설정한 키가 삭제되었을 때 restore key ttl serialized-value REPLACE 를 실행하면 복구됩니다.
// Repalce를 설정하지않았을 때 key가 이미 존재하면 복구가 진행되지 않으며, 설정하였을 때는 dump하였던 key를 replace에 입력한 key에 덮어씁니다.
```

---

## String in Redis

1. set key value [EX secons|PX milliseconds|KEEPTTL] [NX|XX]

- nx를 설정하면 이미 존재하는 키이면 key 설정이 불가능합니다.
- xx를 설정하면 이미 존재하는 key 일때만 설정이 됩니다.

2. append

- append key value
- key의 value에 새로운 vaule를 추가합니다.

3. incr

- incr key
  - key의 value를 1만큼 증가시킵니다.
- incrby key increment
  - key의 value를 increment만큼 증가시킵니다.
- incrbyfloat key increment

4. decr

- decr key
  - 1 감소시킵니다.
- decr key decrement
  - decrement만큼 감소시킵니다.

5. getset

- getset key value
  - key에 새로운 value를 적용시키고 이전의 value를 return 합니다.
  - 이전의 value가 존재하지 않을 때는 nil을 반환합니다.

6. mset

- mset key value [key value ...]
- 한번에 여러개의 key를 생성할 때 사용합니다.

7. mget

- mget key [key ...]
- 한번에 여러개의 key의 value를 나타냅니다.

8. msetnx

- msetnx key value [key value ...]
- key가 이미 존재한다면 0을 반환합니다.

9. getrange

- getrange key start end

10. setex

- setex key seconds value
- set expire을 간편하게 설정해주는 명령어입니다.

11. psetex

- psetex key milliseconds value

12. setrange

- setrange key offset value
- key의 value를 offset위치부터 새로운 value로 저장합니다.

13. strlen

- strlen key
- key의 길이를 반환합니다.

---

## List in Redis

1. lpush key eleoment [element ...]

- 리스트 왼쪽에 값을 집어넣는 명령어 입니다.

2. rpush key element [element ...]

- 리스트 오른쪽에 값을 집어넣는 명령어 입니다.

3. lrange key start end

- key 리스트안 value를 확인하는 명령어입니다.

4. lpushx key value, rpushx key value

- key라는 리스트가 존재할때 만 value를 넣습니다.

5. lpop key, rpop key

- 명령어에 따라 왼쪽,오른쪽 value를 하나 꺼냅니다.

6. ltrim key start stop

- key 리스트에서 start~stop에 해당되는 value 말고는 다 제거합니다.

7. lset key index element

- key 리스트에서 index에 해당하는 값을 element로 설정합니다.

8. lindex key index

- 리스트 key의 index에 위치하는 value를 반환합니다.

9. linsert key BEFORE|AFTER pivot element

- pivot값 전,후 에 element를 삽입합니다.

10. llen key

- 리스트 key의 길이를 반환합니다.

11. lrem key count element

- count가 0보다 클때 head to tail까지 돌면서 element가 존재하면 삭제합니다. element가 여러개일시, count만큼 삭제됩니다.
- count가 0보다 작을시 tail to head 로 적용됩니다.
- count가 0일시 해당하는 element를 다 삭제합니다.

---

## Hashes in Redis

Hash is a map between fields and values
Hashes are the perfect data type to represent objects

1. hset key field value [field value ...]

- hash 생성
  - hsetnx key field value // 같은 이름의 field가 존재하면 value가 적용되지 않습니다.

2. hget key field

- hash 확인

3. hmset key field value [field value ...]

- 버전이 달라서그런지 그냥 hset에서 해도 됩니다.

4. hgetall key

- key의 모든 field value쌍을 보여줍니다.

5. hmget key field [field ...]

- key의 field를 여러개 보여줍니다.

6. hvals key

- hash key의 모든 value를 보여줍니다.

7. hkeys key

- hash key의 모든 field를 보여줍니다.

8. hexists key field

- hash key에 field가 존재하면 1을 반환 존재하지않으면 0을 반환합니다.

9. hlen key

- hash key의 field 개수를 반환합니다.

10. hdel key field [field ...]

- hash key의 field를 삭제합니다.

11. hincrby key field increment

- hash key의 field's value가 integer일시 increment만큼 증가합니다.

12. hincrbyfloat key field increment

13. hstrlen key field

- field's value의 길이를 반환합니다.

---

## Sets in Redis

Sets are an unordered collection of Strings

1. sadd key member [member ...]

- sets를 추가합니다.

2. smembers key

- set의 key를 보여줍니다 sets는 무작위 순서로 저장되지만 한번 저장되면 그 순서는 고정입니다.

3. sismember key member

- sets key에 member가 있으면 1을 반환 없으면 0을 반환합니다.

4. scard key

- sets의 총 member의 수를 알려줍니다.

5. smove source destination member

- source의 member를 destination으로 옮깁니다. 성공하면 1 실패하면 0을 반환합니다.

6. spop key [count]

- 랜덤 member를 count만큼 지웁니다.

7. srem key member [member ...]

- sets key의 member를 지웁니다.

### Operation on Sets

1. sdiff key [key ...]

- key1 - key2 를 반환합니다.

2. sdiff destination key [key ...]

- key1 - key2 를 destination에 저장합니다.

1. sinter key [key ...]

- key1 와 key2의 교집합을 반환합니다.

2. sinterstore destination key [key ...]

- key1 와 key2의 교집합을 destination에 저장합니다.

1. sunion key [key ...]

- key1 + key2 를 반환합니다.

2. sunionstore destination key [key ...]

- key1 + key2 를 destination에 저장합니다.

3. srandmember key [count]

- sets key의 멤버를 랜덤으로 뽑습니다.

### Sorted Sets

Sorted sets are a data type which is similar to a mix between a Set and a Hash

Like sets, sorted sets are composed of unique, non-repeating string elements, so in some sense a sorted set is a set as well.

Sorted sets elements are ordered

Every element in a sorted set is associated with a floating point vlaue, called the score (this is why the type is also similar to a hash, since every element is mapped to a value)

1. zadd key [NX|XX] [CH] [INCR] score member [score member ...]
   ex) zadd students 1 Rob 2 John 3 Smith

- sorted sets를 추가합니다.
- score 은 float이여야 합니다.
- nx를 추가하면 이미 존재하는 member이면 추가되지 않습니다.
  - nx를 추가해도 score은 겹쳐도 member의 이름만 겹치지않으면 추가가 가능합니다.
- xx를 추가하면 member가 이미 존재할때만 적용됩니다.
- Sorted set은 알파벳 순으로 정렬되지않고 score순으로 정렬됩니다. 같은 score안에서는 알파벳 순으로 정렬됩니다.
- ch를 추가하면 몇개가 change 되었는지 반환합니다.
- incr를 추가하면 member의 score에 새로운 score만큼 증가됩니다.
  - ex. 기존 Sono의 score가 1이였을때, zadd key incr 2 Sono = sono의 score가 3이됩니다.

2. zrange key start stop [WITHSCORES]

- sorted sets를 확인합니다.

3. zcard key

- sorted sets인 key의 member의 수를 반환합니다.

4. zrem key member [member ...]

- member를 지웁니다.

5. zscore key member

- member의 score을 반환합니다.

6. zrevrange key start stop [withscores]

- 역순으로 출력해줍니다.

7. zrank key member

- member가 몇번째 인덱스에 있는지 반환해줍니다.

8. zrevrank key member

- zrank를 역순으로 적용합니다.

9. zincrby key increment member

- member의 score을 increment만큼 증가시킵니다.

10. zcount key min max

- score가 min ~ max인 member의 수를 반환합니다.
- zcount name -inf +inf // Sorted sets의 모든 member의 수를 반환합니다.

11. zpopmax key [count]

- count만큼 스코어중 가장큰 값을 제거합니다.

12. zpopmin key [count]

- count만큼 스코어중 가장 작은 값을 제거합니다.

13. zinterstore destination numkeys key [key ...] [WEIGHTS weight] [AGGREGATE SUM|MIN|MAX]

- weight옵션이 주어지지 않았을 때 default값으로 1이 지정됩니다.
- aggregates 옵션이 주어지지 않았을때 default값으로 sum이 지정됩니다.
- ex) z1 = {1: hey, 2: hello}, z2 = {1: bye, 3: hello} 뒤 zinterstore z3 2 z1 z2 weights 5 6 aggregate sum 을 한다고 가정했을 때
- z1, z2를 intersection을 하면 hello가 같습니다 그런데 score가 다릅니다. 여기서 이제 weights 값은 곱하는 계수가 됩니다. 5와 z1의 hello의 score인 2를 곱하고 6과 z2의 hello의 score인 3을 곱합니다. 여기서 Aggregate가 sum이면 곱한 두 수를 더한 결과 값이 destination에 저장되는 것이고 max면 둘 중 큰값, min이면 둘중 작은 값이 저장됩니다.

14. zunionstore destination numkeys key [key ...] [WEIGHT weight] [AGGREGATE SUM|MIN|MAX]

- zinterstore와 동작원리가 같습니다. 합집합으로 적용될 뿐입니다.

15. zrangebyscore key min max [withscores] [limit offset count]

- score가 min~max에 해당하는 elements를 반환합니다.

16. zrangebylex key min max [LIMIT offset count]

- score가 아닌 알파벳 순으로 출력합니다. 여기서 min, max는 숫자가 아니므로 min을 - max를 +로 설정하면 -는 문자의 처음시작 부분 +는 문자의 끝 부분까지를 뜻합니다.
- min max 설정시 그냥 A R을 하면 오류가 뜹니다. 여기서 괄호를 쓰게되는데 [ 은 포함하는 것을 뜻하고 (는 포함하지 않는 것을 뜻합니다. (Alex (Rob 일시 Alex~Rob 사이에 해당하는 알파벳이 출력됩니다.(Alex, Rob은 제외됩니다.)

17. zlexcount key min max

- min~max사이에 해당되는 알파벳을 가진 key의 value의 수를 반환합니다.

18. zrevrangebylex key max min [LIMIT offset count]

- zrangebylex와 같은 원리인데 역순으로 적용됩니다.

19. zremrangebylex key min max

- min~max사이의 알파벳을 가진 key의 value를 삭제합니다.

20. zremrangebyrank key start stop

- start~stop에 해당하는 rank를 가진 key의 value를 삭제합니다 // rank란 index와 같은 개념입니다.

21. zremrangebyscore key min max

- min~max에 해당하는 score를 가진 key의 value를 삭제합니다.

---

## Transaction

Redis 에서 MULTI, EXEC, DISCARD, WATCH 는 Transaction 의 기반이 되는 Command 들이다.

Transaction 에서 모든 Command 들은 순차화되어 순서대로 실행된다. 다른 사용자의 요청은 기존에 실행되고 있던 Redis transaction 중간에 실행될 수 없다. 즉, Redis 에서 Transaction 은 단일 isolated 작업으로써 실행된다는 점이 보장된다.

모든 커맨드가 처리되거나 모두 미처리되는 atomic한 성질을 갖고있습니다.

Redis는 rollback을 지원하지 않습니다.

Rollback이란 하나의 트랜잭션 처리가 비정상적으로 종료되어 트랜잭션의 원자성이 깨진경우, 트랜잭션을 처음부터 다시 시작하거나, 트랜잭션의 부분적으로만 연산된 결과를 다시 취소시키는 것을 말합니다.

1. MULTI : Transaction 시작

- multi를 입력하면 transaction이 실행됩니다. 이 상태에서 명령어를 입력하면 바로 실행되지 않고 QUEUED라고 뜹니다.

2. EXEC : Transaction Commit

- QUEUED라고 반환되었던 명령어들을 실행합니다.
- 순차적으로 실행합니다.

3. DISCARD : Transaction 취소

4. WATCH : 특정 Key 변경 감시 check&set

- watch를 설정한후 트랜잭션 밖에서 watch한 값을 변경한 뒤 트랜잭션 안에서 watch를 설정한 값이 또 변경되는 경우에는 exec를 했을 시 nil이 반환됩니다.
- exec를 실행한 뒤에는 바로 unwatch로 바뀝니다.

5. UNWATCH : 모든 WATCH 취소

- 모든 watch를 취소하기 때문에 argument를 작성할 필요가 없습니다.
- 1번 클라이언트에서 watch를 설정한 후 2번 클라이언트에서 unwatch를 하면 적용이 되지 않습니다.

---

## Publish / Subscribe

일반적인 데이터베이스와는 다르게 레디스는 메시지를 주고, 받는 기능을 제공합니다. Publish 명령으로 보내고, Subscribe 명령으로 받습니다. 통로는 채널(channel)을 이용합니다. 채널은 "SET KEY VALUE"에서 사용하는 'KEY'와 같은 것으로 생각하면 됩니다.

1. publish channel message

- 메세지를 보냈을 때 몇명의 클라이언트가 메세지를 받았는지를 반환합니다.

2. subscribe channel [channel ...]

- 먼저 subscribe channel 명령어를 입력했을 땐 subscribe, channel이름, 몇개의 채널을 subscribe했는지 반환합니다.
- 이미 subscribe한 상태에서 다른 클라이언트가 메세지를 보내면 , message, channel 이름, message 내용 을 반환합니다.

3. psubscribe pattern [pattern ...]

- 패턴을가진 이름의 채널을 다 subscribe합니다
- ex. psubscribe ch\* 일 시에 ch1,ch12, ch~~ 채널에서 오는 메세지는 다 받을 수 있습니다.
- 메세지를 받을경우 "pmessage", "pattern", "channel name", "message"를 반환합니다.

4. pubsub subcommand [argument [argument ...]]

- pubsub numsub ch1
  - 이 명령어는 argument에 몇명이 Subscribe했는지 알려줍니다
  - 하지만 numsub이란 명령어는 psubscribe로 인한 패턴으로 채널을 subscribe한사람은 찾지 못합니다.
- pubsub numpat
  - 이 명령어는 패턴을가진 subscribe를 한 클라이언트가 몇명인지 반환합니다.

---

## Geospatial

Redis uses a common strategy for managing geospatial objects. Foreach longitude and latitude pair, a GeoHash is computed.

A GeoHash is a 52 bit integer value in Redis

The GeoHash standard was created by Gustavo Niiemeyer.

GeoHash encodes positions in a short string of letters and digits
= 내부적으로는 52bit integer로 저장하지만 실제로는 short string of letters and digits으로 저장합니다.

Each GeoHash is stored in the named key. the data type of that key is a sorted set.

The GeoHash is stored as the score, and the name of the point is used as the value of the member.

Valid longitudes are from -180~ to 180 degrees.
Valid latitudes are from -85.05112878 to 85.05112878 degrees.

It just assumes that the Earth is a sphere, since the used distance formula is the Haversine formula

1. geoadd key longitude latitude member [longitude latitude member]

- key에 위도, 경도와 그곳에 해당하는 곳의 member이름을 저장합니다.
- zrange key start end withscore
  - geoadd 는 sorted set으로 저장되기 때문에 zrange로 값을 확인해 보면 member의 이름과 score은 52bit integer value 로 저장됩니다.

2. geohash geopoints member [member ...]

- ex) geohash geopoints Bank 위에서 저장한 key와 member를 geohash 명령어를 실행합니다.
- 실행한 결과는 52bit integer value를 나타내는 짧은 string으로 반환합니다.
- 여기서 얻게된 string을 geohash.org/string 에 접속해보면 같은 위치가 나옵니다.

3. geopos key member [member ...]

- key에 해당하는 member의 longitude, latitude를 반환합니다.

4. geodist key member1 member2 [mi|km|ft|m]

- 거리를 알려줍니다.

5. georadiusbymember key member radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count] [ASC|DESC] [STORE key] [STOREDIST key]

- member와의 거리가 radius(m|km|ft|mi)안에 있는 곳을 반환합니다.
- WITHCOORD = 위도와 경도를 표시해줍니다,
- WITHDIST = 거리를 표시해줍니다.
- WITHHASH = hash를 표시해줍니다.
- Count = 개수를 지정합니다.
- ASC|DESC = 내림차순/오름차순을 정합니다.
- STORE key = store 명령어를 사용할 땐 withcoord, withdist, withhash 명령어는 제거해야합니다.
  - 명령어에 해당하는 member들을 hash와 함꼐 저장합니다.
- STOREDIST key = hash코드가 아닌 거리를 저장합니다.

6. georadius key longitude latitude radius m|km|ft|mi [withcoord] [withdist] [withhash] [count count] [ASC|DESC] [STORE key] [STOREDIST key]

- 5번 명령어와 동일하나 직접 입력한 위도와 경도를 key의 멤버와 비교하는 명령어입니다.

---

## HyperLogLog

HyperLogLog keeps a counter of items that is incremented when new items are added that have not been previously added

The main aim of hyperloglog is to check unique visitors on my Web site not just keeping track of my data

Hyperloglog provides a very low error rate when estimating the unique items of a set

1. pfadd key element [element ...]

- ex) pfadd website Alex Bob Alex Rob
  - website에 Alex, Bob, Alex, Rob visitor가 등록됩니다. 처음 등록된 visitor이면 1이 반환됩니다.
  - 여기서 pfadd website Bob 을하면 bob은 이미 visit하였기 때문에 0을 반환합니다.

2. pfcount key [key ...]

- unique visitor의 수를 반환합니다. 위 예시의 경우 alex, Bob은 2번을 방문했지만 총 방문자의 수는 3명이기 때문에 3명을 반환합니다.

3. pfmerge destkey sourcekey [sourcekey ...]

- destkey에 sourcekey를 합칩니다 합칠 경우 이름이 같은 visitor의 경우엔 count하면 1로 칩니다.

---

## Pipeline in Redis

계속해서 명령어하나하나가 데이터베이스에 전달되는건 좋지않습니다.
그래서 한번에 group해서 데이터베이스에 전달하는 방법이 파이프라인입니다.

```py
pipe = r.pipeline()

for s_id, shirt in shirts.items():
    for field, value in shirt.items():
        pipe.hset(s_id, field, value)

pipe.execute()
```

## Publish / Subscribe 사용 예제

```js
// redis.js

var redis = require("redis");
var subscriber = redis.createClient();
var publisher = redis.createClient();
var msg_count = 0;

// subscriber 객체가 구독을 시작할 때 발생하는 콜백 함수
subscriber.on("subscribe", function (channel, count) {
  // 구독 시작 후 publisher 객체가 발행 하도록 함. (일치하는 채널만)
  publisher.publish("Goorm Channel", "발행자 첫번째 메시지");
  publisher.publish("Goorm Channel", "발행자 두번째 메시지");
  publisher.publish("Goorm Channel", "발행자 마지막 메시지");
});

// subscriber 객체가 메시지를 받으면 호출되는 함수
subscriber.on("message", function (channel, message) {
  console.log("채널명: " + channel + ", 메시지: " + message);
  msg_count += 1;

  // 메시지를 3번 보냈을 시 subscriber 구독 종료, 구독/발행자 종료
  if (msg_count == 3) {
    subscriber.unsubscribe();
    subscriber.end();
    publisher.end();
  }
});

// Goorm Channel의 구독을 시작
subscriber.subscribe("Goorm Channel");
```

## 부가 내용

데이터베이스에 많은 key가 존재할 때, keys \* 명령어는 좋지않습니다.

cursor 값을 0으로 지정한 SCAN/SSCAN/ZSCAN/HSCAN 명령으로 순회가 시작되고, 이어지는 순회에 사용할 cursor 값과, 지정한 패턴(pattern)과 일치하는 키를 최대 지정한 갯수(count)만큼 반환합니다. 반환된 cursor 값이 0이면 순회가 종료됩니다. 이 과정을 전체 순회(full iteration)이라고 합니다. 다음은 CLI에서 SCAN 명령을 사용하여 전체 순회를 하는 예입니다:

1. scan cursor [MATCH pattern] [Count count] [TYPE type]

- ex) scan 0 match check\*
- 먼저 cursor는 0으로 설정하고 시작합니다.
- 이 명령어는 먼저 커서와 key들을 반환합니다.
- 커서에 있는 숫자로 다시 scan명령어를 입력하면 나머지 key들을 반환합니다.
- 커서가 0이 반환되면 모든 pattern에 해당하는 key가 다 반환된 것입니다.
- 많은 key들을 한번에 보여주는 명령어를 사용하면 좋지 않기 때문에 사용하는 명령어입니다.

## 오류 모음

1. redis-server가 열려있어서 새로 서버를 열수없을때

```sh
chaewonjin@chaewonjin-ui-MacBookPro ~ % ps -ef |grep redis
  501 59435     1   0  2:30PM ??         0:30.13 redis-server *:6379
  501 63096 62813   0  9:03AM ttys002    0:00.00 grep redis

chaewonjin@chaewonjin-ui-MacBookPro ~ % kill -9 59435
chaewonjin@chaewonjin-ui-MacBookPro ~ % redis-server
```

이렇게 하면 다시 서버를 껏다가 킬수 있습니다.
