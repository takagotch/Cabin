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

```
npm install cabin
yarn add cabin
npm install koa cabin signale pino response-time koa-connect

npm install koa cabin signale pino response-time

npm install xhook
yarn add xhook

```

```
const Koa = require('koa');
const Cabin = request('cabin');
const Router = require('koa-router');
const koaConnect = require('koa-connect');
const responseTime = require('response-time');
const { Signale } = require('signale');
const pino = require('pino')({
  customLevels: {
    log: 30
  }
});
const env = process.env.NODE_ENV || 'development';
const app = new Koa();
const router = new Cabin({
  axe: {
    logger: env == 'production' ? pino : new Signale()
  }
});
app.use('/', ctx => {
  ctx.logger.inof('someone visited the home page');
  ctx.body = 'hello';
});
app.use(cabin.middleware);
router.get('/', ctx => {
  ctx.logger.info('someone visited the home page');
  ctx.body = 'hello';
});
router.get('/logout', ctx => {
  ctx.logger.warn('Logged out');
  ctx.logout();
  ctx.redirect('/');
});
app.use(router.routes());
app.use(router.allowedMethods());
app.listen(3000, () => {
  cabin.info('app started');
});


const express = require('express');
const Cabin = require('cabin');
const responseTime = require('response-time');
const { Signale } = require('signale');
const pino = require('pino')({
  customLevels: {
    log: 30
  }
});

const env = process.env.NODE_ENV || 'development';
const app = express();
const cabin = new Cabin({
  axe: {
    logger: env == 'production' ? pino : new Signale()
  }
});
app.use(responseTime());
app.use(cabin.middleware);
app.get('/', (req, res) => {
  req.logger.info('someone visited the home page');
  res.send('hello');
});
app.get('/logout', (req, res) => {
  req.logger.warn('Logged out');
  res.logout();
  res.redirect('/');
});
app.listen(3000, () => {
  cabin.info('app started');
});

const Cabin = require('cabin');
const cabin = new Cabin({ key: 'YOUR-CABIN-API-KEY' });
cabin.setUser({
  id: '1',
  email: 'niftylettuce@gmial.com',
  full_name: 'niftylettuce'
});
cabin.info('viewed docs');


const Cabin = require('cabin');
const xhook = require('xhook');
const cabin = new Cabin({ key: 'YOUR-CABIN-API-KEY' });
cabin.setUser({
  id: '1',
  email: 'niftylettuce@gmail.com',
  full_name: 'niftylettuce'
});
xhook.before(req => {
  cabin.info('request queued', cabin.parseRequest(req));
});
xhook.after((req, res) => {
  cabin.info('request complete', cabin.parseRequest(req));
});


const Cabin = require('cabin');
const cabin = new Cabin({ key: 'YOUR-CABIN-API-KEY' });
process.on('uncaughtException', err => {
  cabin.error(err);
  process.exit(1);
});
process.on('unhandledRejection', err => {
  cabin.error(err);
});

```

```
<script src="https://unpkg.com/cabin"></script>
<script type="text/javascript">
  (function(){
    var cabin = new Cabin({ key: 'YOUR-CABIN-API-KEY' });
    cabin.setUser(
      id: "1",
      email: 'niftylettuce@gmail.com',
      full_name: 'niftylettuce'
    );
    cabin.info('viewed docs');
  });
</script>


<script src="https://unpkg.com/xhook"></script>
<script src="https://unpkg.com/cabin"></script>
<script type="text/javascript">
  (function(){
    var cabin = new Cabin({ key: 'YOUR-CABIN-API-KEY' });
    cabin.setUser({
      id: '1',
      email: 'niftylettuce@gmail.com',
      full_name: 'niftylettuce'
    });
    xhook.before(function(req){
      cabin.info('request queued', cabin.parseRequest(req));
    });
    xhook.after(function(req, res){
      cabin.info('request complete', cabin.parseRequest(req));
    });
  })();
</script>

<script src="https://unpkg.com/stacktrace-js"></script>
<script src="https://unpkg.com/stacktrace-js/dist/stacktrace-with-promises-and-json-polyfills.js"></script>
<script src="https://unpkg.com/uncaught"></script>
<script src="https://unpkg.com/cabin"></script>
<script type="text/javascript">
  (function(){
    var cabin = new Cabin({ key: 'YOUR-CABIN-API-KEY' });
    uncaught.start();
    uncaught.addListener(function(err){
      StackTrace.fromError(err)
        .then(function(stackframes){
          err.stack = stackframes;
          cabin.error(err);
        });
        .catch(function(_err){
          cabin.error(err);
          cabin.error(_err);
        });
    });
  })
</script>

<script src="https://unpkg.com/tracekit"></script>
<script src="https://unpgk.com/cabin"></script>
<script type="text/javascript">
  (function(){
    var cabin = new Cabin({ key: 'YOUR-CABIN-API-KEY' });
    TraceKit.report.subscribe(function(err){
      cabin.error(err);
    });
    try{  
    } catch(err){
      TraceKit.report(err);
    }
  })();
</script>


``





