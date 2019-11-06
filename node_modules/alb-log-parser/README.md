# alb-log-parser

A basic parser for ALB access logs, forked from elb log parser git@github.com:toshihirock/node-elb-log-parser.git
i cannot find alb log parser instead of elb-log-parser. so i modify a bit of the code. Thank you toshihirock!

## When I use this npm?

+ ALB Access Log(S3)->Lambda->ElasticSearch. Example [awslabs/amazon-elasticsearch-lambda-samples](https://github.com/awslabs/amazon-elasticsearch-lambda-samples/blob/master/src/s3_lambda_es.js)
+ Analyze ELB Access Log

## Install

```
npm install -g alb-log-parser
```


## Example API usage

```
node-alb-log-parser$node
> var parse = require('./index');
undefined
> parse('http 2015-05-13T23:39:43.945958Z my-loadbalancer 192.168.131.39:2817 10.0.0.1:80 0.000086 0.001048 0.001337 200 200 0 57 "GET https://mytest-111.ap-northeast-1.elb.amazonaws.com:443/p/a/t/h?foo=bar&hoge=fuga HTTP/1.1" "curl/7.38.0" DHE-RSA-AES128-SHA TLSv1.2 arn:aws:elasticloadbalancing:us-west-2:123456789012:targetgroup/my-targets/73e2d6bc24d8a067 "Root=1-58337262-36d228ad5d99923122bbe354"')
{ type: 'http',
  timestamp: '2015-05-13T23:39:43.945958Z',
  elb: 'my-loadbalancer',
  client: '192.168.131.39',
  client_port: 2817,
  target: '10.0.0.1',
  request_processing_time: 0.000086,
  target_processing_time: 0.001048,
  response_processing_time: 0.001337,
  elb_status_code: 200,
  target_status_code: 200,
  received_bytes: 0,
  sent_bytes: 57,
  request: 'GET https://mytest-111.ap-northeast-1.elb.amazonaws.com:443/p/a/t/h?foo=bar&hoge=fuga HTTP/1.1',
  user_agent: 'curl/7.38.0',
  ssl_cipher: 'DHE-RSA-AES128-SHA',
  ssl_protocol: 'TLSv1.2',
  target_group_arn: 'arn:aws:elasticloadbalancing:us-west-2:123456789012:targetgroup/my-targets/73e2d6bc24d8a067',
  trace_id: 'Root=1-58337262-36d228ad5d99923122bbe354',
  target_port: 80,
  request_method: 'GET',
  request_uri: 'https://mytest-111.ap-northeast-1.elb.amazonaws.com:443/p/a/t/h?foo=bar&hoge=fuga',
  request_http_version: 'HTTP/1.1',
  request_uri_scheme: 'https:',
  request_uri_host: 'mytest-111.ap-northeast-1.elb.amazonaws.com',
  request_uri_port: 443,
  request_uri_path: '/p/a/t/h',
  request_uri_query: 'foo=bar&hoge=fuga' }
>
```

You get the idea.

## Tests

```
$npm test
```

## License

WTFPL
