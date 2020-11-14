---
layout: default
title: Sidekiq
parent: Rails
nav_order: 3
---

# Sidekiq Cheatsheet

---

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

Queue all scheduled jobs immediately:

```rb
ss = Sidekiq::ScheduledSet.new

ss.each do |job|
  job.reschedule(Time.now)
end
```
