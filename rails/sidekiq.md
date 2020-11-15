---
layout: default
title: Sidekiq
parent: Rails
nav_order: 3
---

# Sidekiq Cheatsheet

---

## References

- Website: [https://sidekiq.org/](https://sidekiq.org/)
- Github: [https://github.com/mperham/sidekiq](https://github.com/mperham/sidekiq)
- Guide: [https://github.com/mperham/sidekiq/wiki](https://github.com/mperham/sidekiq/wiki)

## ActiveJob

Config Sidekiq as queue adapter

```rb
class Application < Rails::Application
  # ...
  config.active_job.queue_adapter = :sidekiq
end
```

An example job

```rb
class ExampleJob < ActiveJob::Base
  queue_as :default
  # Available for Sidekiq 6.0.1+ and Rails 6.0.1+
  sidekiq_options retry: 5

  def perform(*args)
    # Perform Job
  end
end
```

Different calls

```rb
# queue a job
ExampleJob.perform_later(args)
ExampleJob.set(wait_until: Date.tomorrow.noon).perform_later(args)

# Sidekiq job ID
job = ExampleJob.perform_later(args)
jid = job.provider_job_id
```

## Sidekiq API

Reset stats

```rb
Sidekiq::Stats.new.reset
```

Retries queue stats and reset

```rb
rs = Sidekiq::RetrySet.new
rs.size
rs.clear
```

Dead jobs stats and reset

```rb
ds = Sidekiq::DeadSet.new
ds.size
ds.clear
```

Scheduled jobs stats and reset

```rb
ss = Sidekiq::ScheduledSet.new
ds.size
ds.clear
```

Queue all scheduled jobs immediately

```rb
ss = Sidekiq::ScheduledSet.new
ss.each do |job|
  job.reschedule(Time.now)
end
```
