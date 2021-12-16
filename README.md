# jsonnet_demo

## Pre-requistes

- https://github.com/google/jsonnet or https://github.com/google/go-jsonnet
- https://github.com/jsonnet-bundler/jsonnet-bundler

## Steps followed

- `jb init` to create an empty jsonnetfile.json

- `jb install github.com/prometheus-operator/prometheus-operator@v0.52.1`

- Create `main.jsonnet` with following content just to evaulate the jsonnet mixin from prometheus-operator

  ```jsonnet
  (import 'github.com/prometheus-operator/prometheus-operator/jsonnet/mixin/alerts.jsonnet')
  ```

- Run `jsonnet -J vendor main.jsonnet` to generate json file
  - `-J vendor` is specified for jsonnet to search library in this location since we had pulled library using `jb`

- To generate yaml from this json use `gojsontoyaml` [utility](https://github.com/brancz/gojsontoyaml)


  ```go
  jsonnet -J vendor main.jsonnet|gojsontoyaml`
  ```
