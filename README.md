# fyaml
FYAML: Decompose any large YAML document into multiple files

FYAML is convention for breaking any large YAML file into a meaningfully-organized and well-sized set of directories and files.

## What problem does FYAML solve?
Many configuration formats use YAML today. As those YAML files get larger they become unwieldy. Breaking code apart into separate files, especially when those files and directories are named meaningfully, can help make large YAML document more manageable and easier to reason about.

In general, FYAML is intended be useful to delivery a set of files that are destined to be collapsed into a single YAML configuration string that is fed into a platform as a single document.

## Why does it matter that FYAML is "semantic-agnostic"?
FYAML was originally designed as part of the [CirleCI CLI](https://github.com/CircleCI-Public/circleci-cli) `config pack` command, but it is not specific to that format. We didn't want to bake any of our configuration semantics into config packing because we knew they would change over time, and we didn't want to have to make changes to config packing every time we add a new element to our configuration. Also, breaking files apart is a code-maintenance concern, not a semantic issue. FYAML was conceived to allow any semantics to be broken out into directories and file names that reflect that semantics without changing the implementation of FYAML itself.

## How does it work?

Let's say you have the following file system structure:
```
examples/simple/root/
├── bar
│   └── baz.yml
└── subtree
    └── @trees.yml
```

An FYAML implementation, when given the path to `examples/simple/root/` as input, would return the following YAML document:
```
bar:
  baz:
    anotherkey: Some value
    somekey:
    - value1
    - value2
subtree:
  ginkgo:
    seasonality: deciduous
  oak:
    seasonality: deciduous
  pine:
    seasonality: evergreen
```

## Where can I learn about the details?

See the [fyaml-specification.md](fyaml-specification.md) file in this repository for details.

