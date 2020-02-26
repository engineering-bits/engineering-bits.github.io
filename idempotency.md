# Idempotency

Operation is **idempotent** if it can be applied multiple times and result doesn't change.


For example in REST:
* GET, UPDATE, DELETE methods assumed idempotent. They will result in exactly the same result if executed multiple times.
* POST is NOT idempotent, calling it multiple times will create multiple entities.


Why it matters in distributed systems:
* A call from Service A to Service B might fail, and be retried. You need to know what happens in this case.
* Event processing (like Kafka) is often used in At Least Once mode, which means your listener might be called more than once for each event, so it must be idempotent.
* Workflow orchestration (like SWF or StepFunctions or Conductor) assume activities/workers are idempotent.

Recommended reading:
https://stripe.com/blog/idempotency
