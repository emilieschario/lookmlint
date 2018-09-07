# lookmlint

Lint your lookML.

Includes linting for catching the following:

- Unused view files
- Unused `include`s in explorations
- Views without a primary key
- Raw SQL field references in join conditions (e.g. `order.id` vs `${order.id}`)

You can optionally configure `lookmlint` to keep labels clean throughout your project, catching:

- Improperly-capitalized acronyms (e.g. 'Sla')
- Abbreviations (e.g. 'Num')

## installation

```
$ git clone git@github.com:warbyparker/lookmlint.git
$ pip install -e ./lookmlint
```

### lookml-parser dependency

This project invokes and relies on outputs generated by the awesome [lookml-parser](https://www.npmjs.com/package/lookml-parser) tool, which parses a lookML repo and outputs the results as `json`.

Ensure this is installed to get `lookmlint` to work properly:

```
$ npm install -g lookml-parser
```

## usage

From the CLI:

```
$ lookmlint lint ~/my-lookml-repo
```

From python:

```python
import lookmlint
lookmlint.lint('~/my-lookml-repo')
```

### configuration

`lookmlint` looks for a file named `.lintconfig.yml` in your lookML project repo.

Its' contents can contain lists of abbreviations and/or acronyms you'd like to flag.

#### sample .lintconfig.yml

```yml
abbreviations:
  - num
  - qty
acronyms:
  - aov
  - sms
  - sku
  - sla
```
