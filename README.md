# serverless-framework-template

# set up

1. build

- build main.go with select path

```.shell
GOOS=linux GOARCH=amd64 go build -o main main.go
```

2. deploy

deploy with select region

```
serverless deploy --region ap-northeast-1
```

after deploy command, lambda name will be following.

```
// correcponding definition of serverless.yml {self:service}-${self:provider.stage}-${func name}
// service: go-serverless
// functions:
//   hello:
// => go-serverless-dev
```

3. exec lambda API
you can exec function, on AWS console, but also CLI.
It'll create `out` file in current directory, that include api outputs.

```
aws lambda invoke --function-name <function name>  out --log-type Tail

// if your aws configure default region not matched lambda's region, need specify region
aws lambda invoke --function-name <function name> --region ap-northeast-1 out --log-type Tail

// ex
aws lambda invoke --function-name go-serverless-dev-hello  out --log-type Tail
```
# reference

[official serverless framework](https://www.serverless.com/)

[official go serverless resource](https://www.serverless.com/examples?prod_EXAMPLES_SEARCH_GROWTH%5BrefinementList%5D%5Blanguage%5D%5B0%5D=go)

[AWS reference](https://docs.aws.amazon.com/lambda/latest/dg/golang-handler.html)
