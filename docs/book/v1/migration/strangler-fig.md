# Strangler Fig Pattern or Incremental Migration

The Strangler Fig Pattern is a software migration strategy that implies gradually replacing parts of the old application with new components until the old application is not needed any more.

## How It Works

- Wrap the old application with a routing layer that enables you to selectively redirect incoming requests to either the old code or to new code.
- Choose an existing feature or service and build it in the new architecture.
This applies to new features, as well.
- Replace old features as they are ready to be deployed.
After development and testing is complete on the new code, reroute traffic for that feature or service to the new code.
- Decommission the old application.
Once all features and/or services are migrated, you can shut down the legacy code completely.

## Pluses

- Lower risk – Each change is small, and thus easier to manage and test.
- Continuous delivery – Users and stakeholders see improvements throughout the development process.
- Easier rollback – If the new code doesn't work as intended, reroute traffic back to the old code until the new one is revised.
- Better learning – You discover and fix problems early, adapt your plan more dynamically, and understand the business logic better.

## Conclusion

The Strangler Fig Pattern is the recommended way to go for legacy applications, especially complex ones where a full rewrite would take years and/or millions of dollars.
You mitigate downtime and risk by handling small, easily manageable sections of code at any given time.
One restriction for this pattern is that you need to be able to intercept requests and redirect execution.
The development team can be smaller (since you isolate sections of code you work on) and the development schedule is more adaptable (you can stop at any time because the old application is always there).
