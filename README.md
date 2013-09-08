FUNCTIONS LOVE YAML
===================

FLY is **reactive** **dataflow** **functional** programming language.
You can think of it bit like a spreadsheet, but orgnaized as a tree instead of a table.

FLY is a *ractive* language. Like a spreadsheet, when any cell changes all other dependent cells are immediately effected. Cells can be linked to external sources as well, such as webpage fields. This create a very dynamic user faces system with very little overhead.

## Status

FLY is very pre-alpha. Basically the whole language is in the conceptual stage. Being brain-stormed out of the initial concept of a spreadsheet-like dataflow language using YAML as it its base structure.


## Basics

#### Single Assignment

The underlying programming languge is a single-assignment langauge, and not just mildly so. Consider the simple example:

```yaml
    avg: !fn
      a: !num @1
      b: !num @2
      sum: a + b
      avg: sum / 2
```

The defintion starts with typecasts. `@1` and `@2` refer to the functions parameters. So there are two parameters, they are expected to be numbers and  are assigned to the cells `a` and `b`, respectively. Then the sum of `a` and `b` is calculated. And finally the average is calculated. There are two *important* things to notice about the program.

1. The order of the entries don't actually matter.
2. Input parameters can only occur in typcast entries.
3. Only one operation can be called per entry.

The last point may be overly strict, and may ultimately be dropped. But it is there to make a very important point about the structire of FLY code and will alwasy remain a strong cenvention --FLY programs are intended to be fully *deconstructed* into *named* parts. What happens then is that the language can start to talk about itself at a very fine grain level, for example, one of the things we might do with that is [AOP]().

#### Conditions

Writing considitions in FLY is actually rather pleasent. And `!if` type is an ordered map (omap) of predicate-result entries. 

```yaml
    highest: !fn
      a: !num @1 
      b: !num @2
      d: a > b
      *: !if
        - d: a
        - b
```

#### Signals

We can sync with external signal.

```yaml
    click: !signal
      mouse.click
```

## Note

The current prototype is out-of-date with the current design concepts. The prototype is written in Ruby and has a simple Forth-like scripting language. Cells functions can also be scripted in Ruby. )


