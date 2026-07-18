# eval

An arbitrary expression evaluator for Go. Parses a string expression once into an
`EvaluableExpression`, then evaluates it repeatedly against a set of named parameters,
returning a single `interface{}` result.

Supports arithmetic, comparison, logical, bitwise, ternary, and string operators;
regular-expression matching; membership (`in`); parameter accessors that reach into
struct fields and map keys (`obj.Field`); and user-defined functions.

```go
expr, err := eval.NewEvaluableExpression("foo > 0 && bar in ('a', 'b')")
result, err := expr.Evaluate(map[string]interface{}{"foo": 1, "bar": "a"})
// result == true
```

For a stable set of custom functions, build with
`eval.NewEvaluableExpressionWithFunctions`. To supply parameters lazily, pass any
value implementing the `Parameters` interface to `Eval`.

## Provenance

Taken from `github.com/casbin/govaluate` v1.3.0, itself a fork of
`github.com/Knetic/govaluate` by George Lester. See NOTICE for the full lineage and
LICENSE for the MIT terms.
