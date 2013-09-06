FUNCTIONS LOVE YAML
===================

FLY is **reactive** **dataflow** **functional** programming language.
You can think of it bit like a spreadsheet, but orgnaized as a tree instead of a table.

FLY is a *ractive* language. Like a spreadsheet, when any cell changes all other dependent cells are immediately effected. Cells can be linked to external sources as well, such as webpage fields. This create a very dynamic user faces system with very little overhead.

## Basics

The underlying programming languge is a single-assignment langauge, and not just mildly so. Consider the simple example:

```yaml
    avg: !fn
      a: !num @1
      b: !num @2
      sum: @a + @b
      avg: @sum / 2
```

The defintion starts with typecasts. `@1` and `@2` refer to the functions parameters. So there are two parameters, they are expected to be numbers and  are assigned to the cells `a` and `b`, respectively. Then the sum of `a` and `b` is calculated. And finally the average is calculated. There are two *important* things to notice about the program.

1. Input parameters can only occur in typcast entries.
2. Only one operation can be called per entry.
3. The order of the entries don't actually matter.


### Conditions

```yaml
    highest: !fn
      a: !num @1 
      b: !num @2
      d: a > b
      *: !if
        - d: a
        - b
```

### Signals

We can sync with external signal.

    TODO


## Note

The current prototype is out-of-date with the current design concepts. The prototype is written in Ruby and has a simple Forth-like scripting language. Cells functions can also be scripted in Ruby. )


