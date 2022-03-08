## Joi

Joi는 joi는 Object schema validator라고 합니다

```js
const InquiryPostValidationSchema = Joi.object().keys({
  name: Joi.string().required().max(100),
  phone: Joi.string().required().min(10).max(11),
  message: Joi.string().required().max(5000),
});

router.post("/", async (ctx) => {
  const inquiryRepository = getCustomRepository(InquiryRepository);

  const {
    value: { name, phone, message },
    error,
  } = InquiryPostValidationSchema.validate(ctx.request.body);
  if (error) throw ctx.throw(400, error);

  const inquiry = inquiryRepository.create({ name, phone, message });
  const createdInquiry = await inquiryRepository.save(inquiry);
  ctx.body = createdInquiry;
});
```
