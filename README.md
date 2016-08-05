# stability-badges

SVG badges for Go projects.

## Badges

### Experimental
![stability-experimental](https://img.shields.io/badge/stability-experimental-orange.svg)

This API is so immature that offering any kind of API stability guarantees would be unreasonable. The use of these packages as dependencies of stable packages and applications is discouraged.

Packages should not remain _Experimental_ for too long, as the lack of API stability hinders their adoption, and hurts the stability of packages and applications that depend on them.

```markdown
[![stability-experimental](https://img.shields.io/badge/stability-experimental-orange.svg)](https://github.com/emersion/stability-badges#experimental)
```

### Unstable
![stability-unstable](https://img.shields.io/badge/stability-unstable-yellow.svg)

This API is not stable yet, but backwards-compatibility will be maintained if possible.

```markdown
[![stability-unstable](https://img.shields.io/badge/stability-unstable-yellow.svg)](https://github.com/emersion/stability-badges#unstable)
```

### Stable
![stability-stable](https://img.shields.io/badge/stability-stable-green.svg)

This API is stable and backwards-compatibility is guaranteed.

```markdown
[![stability-stable](https://img.shields.io/badge/stability-stable-green.svg)](https://github.com/emersion/stability-badges#stable)
```

Examples of modifications that DO NEED a major version change are:
* Removing or renaming *any* exposed name (function, method, type, etc)
* Adding, removing or renaming methods in an interface
* Adding a parameter to a function, method, or interface
* Changing the type of a parameter or result in a function, method, or interface
* Changing the number of results in a function, method, or interface
* Some struct changes (see details below) 

On the other hand, the following modifications are FINE WITHOUT a major version change:
* Adding exposed names (function, method, type, etc)
* Renaming a parameter or result of a function, method, or interface
* Some struct changes (see details below) 

Note that some of these changes may still break code that depends on details of the existing API due to the use of reflection. These uses are considered an exception, and authors of such packages will have to follow the development of dependend upon packages more closely.

#### Compatibility on struct changes

Adding a field to a struct may be safe or not depending on how the struct was previously defined.

A struct containing non-exported fields may always receive new exported fields safely, as the language disallows code outside the package from using literals of these structs without naming the fields explicitly.

A struct with a significant number of fields is likely safe as well, as it's inconvenient to be both written and read without naming the fields explicitly.

A struct consisting only of a few exported fields must not have fields added (exported or not) or repositioned without a major version change, as that will break code using such structs in literals with positional fields.

Removing or renaming exported fields from an existing struct is of course a compatibility breaking change.

### Frozen
![stability-frozen](https://img.shields.io/badge/stability-frozen-brightgreen.svg)

This API will not change anymore at all.

```markdown
[![stability-frozen](https://img.shields.io/badge/stability-frozen-blue.svg)](https://github.com/emersion/stability-badges#frozen)
```

### Deprecated
![stability-deprecated](https://img.shields.io/badge/stability-deprecated-red.svg)

This API is not maintained and should not be used anymore.

```markdown
[![stability-deprecated](https://img.shields.io/badge/stability-deprecated-red.svg)](https://github.com/emersion/stability-badges#deprecated)
```

## Credits

Basically https://github.com/orangemug/stability-badges adapted for Go thanks to http://labix.org/gopkg.in
