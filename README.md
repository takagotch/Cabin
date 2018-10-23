### Cabin
---
.rb
https://github.com/jordansissel/ruby-cabin
.js
https://github.com/bitnami-labs/cabin

https://github.com/cabinjs/cabin

.rb
```ruby
logger.error("#{hostname} #{program}[#{pid}]: error: PAM: authentication error for illegal user #{user} from #{client}")

logger.error("PAM: authentication error for illegal user", {
  :hostname => "fbsd1",
  :program => "sshd",
  :pid => 4374,
  :user => "amelia",
  :client => "xxxxxxxxxx.doin.ne.jp"
})

n = 30
logger[:input] = n
logger.time("gibnacci duration") do
  fib(30)
end

metrics = Cabin::Channel.new
logger = Cabin::Channel.new

begin
  logger.time("Handling request") do
    handle_request
  end
  metrics[:hits] += 1
rescue => e
  metrics[:errors] += 1
  logger.error("An error occurred", :exception => e, :backtrace => e.backtrace)
end

```

```json
{
  "timestamp": "2011-09-25T13:44:37.034Z"
  "message": "PAM: authentication error for illegal user",
  "hostname": "fbsd1",
  "program": "sshd",
  "pid": 4374,
  "user": "amelia",
  "client": "xxxxxxxx.dion.ne.jp"
}

```
---
.js

