
<!--
DO NOT EDIT THIS FILE
It has been generated from the template `README.md.eex` by Extractly (https://github.com/RobertDober/extractly.git)
and any changes you make in this file will most likely be lost
-->

# Earmark—A Pure Elixir Markdown Processor

[![CI](https://github.com/pragdave/earmark/actions/workflows/ci.yml/badge.svg)](https://github.com/pragdave/earmark/actions/workflows/ci.yml)
[![Coverage Status](https://coveralls.io/repos/github/pragdave/earmark/badge.svg?branch=master)](https://coveralls.io/github/pragdave/earmark?branch=master)
[![Hex.pm](https://img.shields.io/hexpm/v/earmark.svg)](https://hex.pm/packages/earmark)
[![Hex.pm](https://img.shields.io/hexpm/dw/earmark.svg)](https://hex.pm/packages/earmark)
[![Hex.pm](https://img.shields.io/hexpm/dt/earmark.svg)](https://hex.pm/packages/earmark)


**N.B.**

This README contains the docstrings and doctests from the code by means of [extractly](https://hex.pm/packages/extractly)
and the following code examples are therefore verified with `ExUnit` doctests.

## Table Of Content

- [Table Of Content](#table-of-content)
- [Options](#options)
  - [Earmark.Cli.Implementation](#earmarkcliimplementation)
  - [Earmark.Options](#earmarkoptions)
  - [Earmark.Options.make_options/1](#earmarkoptionsmake_options1)
  - [Earmark.Options.relative_filename/2](#earmarkoptionsrelative_filename2)
  - [Earmark.Options.with_postprocessor/2](#earmarkoptionswith_postprocessor2)
  - [Earmark.Internal](#earmarkinternal)
  - [Earmark.Internal.as_ast!/2](#earmarkinternalas_ast2)
  - [Earmark.Internal.from_file!/2](#earmarkinternalfrom_file2)
  - [Earmark.Internal.include/2](#earmarkinternalinclude2)
  - [Earmark.Transform](#earmarktransform)
    - [Transformers](#transformers)
    - [Postprocessors and Convenience Functions](#postprocessors-and-convenience-functions)
- [Contributing](#contributing)
- [Author](#author)

## Options


### Earmark.Cli.Implementation

Functional (with the exception of reading input files with `Earmark.File`) interface to the CLI
returning the device and the string to be output.


### Earmark.Options

This is a superset of the options that need to be passed into `EarmarkParser.as_ast/2`

The following options are proper to `Earmark` only and therefore explained in detail

- `compact_output`: boolean indicating to avoid indentation and minimize whitespace
- `eex`: Allows usage of an `EEx` template to be expanded to markdown before conversion
- `file`: Name of file passed in from the CLI
- `line`: 1 but might be set to an offset for better error messages in some integration cases
- `smartypants`: boolean use [Smarty Pants](https://daringfireball.net/projects/smartypants/) in the output
- `ignore_strings`, `postprocessor` and `registered_processors`: processors that modify the AST returned from

   EarmarkParser.as_ast/`2` before rendering (`post` because preprocessing is done on the markdown, e.g. `eex`)
   Refer to the moduledoc of Earmark.`Transform` for details

All other options are passed onto EarmarkParser.as_ast/`2`

### Earmark.Options.make_options/1

Make a legal and normalized Option struct from, maps or keyword lists

Without a param or an empty input we just get a new Option struct

```elixir
    iex(1)> { make_options(), make_options(%{}) }
    { {:ok, %Earmark.Options{}}, {:ok, %Earmark.Options{}} }
```

The same holds for the bang version of course

```elixir
    iex(2)> { make_options!(), make_options!(%{}) }
    { %Earmark.Options{}, %Earmark.Options{} }
```


We check for unallowed keys

```elixir
    iex(3)> make_options(no_such_option: true)
    {:error, [{:warning, 0, "Unrecognized option no_such_option: true"}]}
```

Of course we do not let our users discover one error after another

```elixir
    iex(4)> make_options(no_such_option: true, gfm: false, still_not_an_option: 42)
    {:error, [{:warning, 0, "Unrecognized option no_such_option: true"}, {:warning, 0, "Unrecognized option still_not_an_option: 42"}]}
```

And the bang version will raise an `Earmark.Error` as excepted (sic)

```elixir
    iex(5)> make_options!(no_such_option: true, gfm: false, still_not_an_option: 42)
    ** (Earmark.Error) [{:warning, 0, "Unrecognized option no_such_option: true"}, {:warning, 0, "Unrecognized option still_not_an_option: 42"}]
```

### Earmark.Options.relative_filename/2

Allows to compute the path of a relative file name (starting with `"./"`) from the file in options
and return an updated options struct

```elixir
    iex(6)> options = %Earmark.Options{file: "some/path/xxx.md"}
    ...(6)> options_ = relative_filename(options, "./local.md")
    ...(6)> options_.file
    "some/path/local.md"
```

For your convenience you can just use a keyword list

```elixir
    iex(7)> options = relative_filename([file: "some/path/_.md", breaks: true], "./local.md")
    ...(7)> {options.file, options.breaks}
    {"some/path/local.md", true}
```

If the filename is not absolute it just replaces the file in options

```elixir
    iex(8)> options = %Earmark.Options{file: "some/path/xxx.md"}
    ...(8)> options_ = relative_filename(options, "local.md")
    ...(8)> options_.file
    "local.md"
```

And there is a special case when processing stdin, meaning that `file: nil` we replace file
verbatim in that case

```elixir
    iex(9)> options = %Earmark.Options{}
    ...(9)> options_ = relative_filename(options, "./local.md")
    ...(9)> options_.file
    "./local.md"
```


### Earmark.Options.with_postprocessor/2

A convenience constructor



### Earmark.Internal

All public functions that are internal to Earmark, so that **only** external API
functions are public in `Earmark`

### Earmark.Internal.as_ast!/2

A wrapper to extract the AST from a call to `EarmarkParser.as_ast` if a tuple `{:ok, result, []}` is returned,
raise errors otherwise

```elixir
    iex(1)> as_ast!(["Hello %% annotated"], annotations: "%%")
    [{"p", [], ["Hello "], %{annotation: "%% annotated"}}]
```

```elixir
    iex(2)> as_ast!("===")
    ** (Earmark.Error) [{:warning, 1, "Unexpected line ==="}]
```


### Earmark.Internal.from_file!/2

This is a convenience method to read a file or pass it to `EEx.eval_file` if its name
ends in  `.eex`

The returned string is then passed to `as_html` this is used in the escript now and allows
for a simple inclusion mechanism, as a matter of fact an `include` function is passed 


### Earmark.Internal.include/2

A utility function that will be passed as a partial capture to `EEx.eval_file` by
providing a value for the `options` parameter

```elixir
    EEx.eval(..., include: &include(&1, options))
```

thusly allowing

```eex
  <%= include.(some file) %>
```

where `some file`  can be a relative path starting with `"./"`

Here is an example using [these fixtures](https://github.com/pragdave/earmark/tree/master/test/fixtures)

```elixir
    iex(3)> include("./include/basic.md.eex", file: "test/fixtures/does_not_matter")
    "# Headline Level 1\n"
```

And here is how it is used inside a template

```elixir
    iex(4)> options = [file: "test/fixtures/does_not_matter"]
    ...(4)> EEx.eval_string(~s{<%= include.("./include/basic.md.eex") %>}, include: &include(&1, options))
    "# Headline Level 1\n"
```


### Earmark.Transform

#### Transformers

For the convenience of processing the output of `EarmarkParser.as_ast` we expose two mappers.

##### `map_ast`

takes a function that will be called for each node of the AST, where a leaf node is either a quadruple of `{tag, attributes, children, meta}`
like `{"code", [{"class", "inline"}], ["some code"], %{}}` or a text leaf like `"some code"`

The result of the function call must be:

- for nodes → a quadruple. The quadruple replace the node. If the children are not intended to be modified, that quadruple element may be `nil`.

- for strings → strings

A third parameter `ignore_strings` which defaults to `false` can be used to avoid invocation of the mapper
function for text nodes

As an example let us transform an ast to have symbol keys

```elixir
      iex(1)> input = [
      ...(1)> {"h1", [], ["Hello"], %{title: true}},
      ...(1)> {"ul", [], [{"li", [], ["alpha"], %{}}, {"li", [], ["beta"], %{}}], %{}}]
      ...(1)> map_ast(input, fn {t, a, _, m} -> {String.to_atom(t), a, nil, m} end, true)
      [ {:h1, [], ["Hello"], %{title: true}},
        {:ul, [], [{:li, [], ["alpha"], %{}}, {:li, [], ["beta"], %{}}], %{}} ]
```

**N.B.** If this returning convention is not respected `map_ast` might not complain, but the resulting
transformation might not be suitable for `Earmark.Transform.transform` anymore. From this follows that
any function passed in as value of the `postprocessor:` option must obey to these conventions.

##### `map_ast_with`

this is like `map_ast` but like a reducer an accumulator can also be passed through.

For that reason the function is called with two arguments, the first element being the same value
as in `map_ast` and the second the accumulator. The return values need to be equally augmented
tuples.

A simple example, annotating traversal order in the meta map's `:count` key, as we are not
interested in text nodes we use the fourth parameter `ignore_strings` which defaults to `false`

```elixir
       iex(2)>  input = [
       ...(2)>  {"ul", [], [{"li", [], ["one"], %{}}, {"li", [], ["two"], %{}}], %{}},
       ...(2)>  {"p", [], ["hello"], %{}}]
       ...(2)>  counter = fn {t, a, _, m}, c -> {{t, a, nil, Map.put(m, :count, c)}, c+1} end
       ...(2)>  map_ast_with(input, 0, counter, true)
       {[ {"ul", [], [{"li", [], ["one"], %{count: 1}}, {"li", [], ["two"], %{count: 2}}], %{count: 0}},
         {"p", [], ["hello"], %{count: 3}}], 4}
```

#### Postprocessors and Convenience Functions

These can be declared in the fields `postprocessor` and `registered_processors` in the `Options` struct,
`postprocessor` is prepened to `registered_processors` and they are all applied to non string nodes (that
is the quadtuples of the AST which are of the form `{tag, atts, content, meta}`

All postprocessors can just be functions on nodes or a `TagSpecificProcessors` struct which will group
function applications depending on tags, as a convienience tuples of the form `{tag, function}` will be
transformed into a `TagSpecificProcessors` struct.

```elixir
    iex(3)> add_class1 = &Earmark.AstTools.merge_atts_in_node(&1, class: "class1")
    ...(3)> m1 = Earmark.Options.make_options!(postprocessor: add_class1) |> make_postprocessor()
    ...(3)> m1.({"a", [], nil, nil})
    {"a", [{"class", "class1"}], nil, nil}
```

We can also use the `registered_processors` field:

```elixir
    iex(4)> add_class1 = &Earmark.AstTools.merge_atts_in_node(&1, class: "class1")
    ...(4)> m2 = Earmark.Options.make_options!(registered_processors: add_class1) |> make_postprocessor()
    ...(4)> m2.({"a", [], nil, nil})
    {"a", [{"class", "class1"}], nil, nil}
```

Knowing that values on the same attributes are added onto the front the following doctest demonstrates
the order in which the processors are executed

```elixir
    iex(5)> add_class1 = &Earmark.AstTools.merge_atts_in_node(&1, class: "class1")
    ...(5)> add_class2 = &Earmark.AstTools.merge_atts_in_node(&1, class: "class2")
    ...(5)> add_class3 = &Earmark.AstTools.merge_atts_in_node(&1, class: "class3")
    ...(5)> m = Earmark.Options.make_options!(postprocessor: add_class1, registered_processors: [add_class2, {"a", add_class3}])
    ...(5)> |> make_postprocessor()
    ...(5)> [{"a", [{"class", "link"}], nil, nil}, {"b", [], nil, nil}]
    ...(5)> |> Enum.map(m)
    [{"a", [{"class", "class3 class2 class1 link"}], nil, nil}, {"b", [{"class", "class2 class1"}], nil, nil}]
```

We can see that the tuple form has been transformed into a tag specific transformation **only** as a matter of fact, the explicit definition would be:

```elixir
    iex(6)> m = make_postprocessor(
    ...(6)>   %Earmark.Options{
    ...(6)>     registered_processors:
    ...(6)>       [Earmark.TagSpecificProcessors.new({"a", &Earmark.AstTools.merge_atts_in_node(&1, target: "_blank")})]})
    ...(6)> [{"a", [{"href", "url"}], nil, nil}, {"b", [], nil, nil}]
    ...(6)> |> Enum.map(m)
    [{"a", [{"href", "url"}, {"target", "_blank"}], nil, nil}, {"b", [], nil, nil}]
```

We can also define a tag specific transformer in one step, which might (or might not) solve potential performance issues
when running too many processors

```elixir
    iex(7)> add_class4 = &Earmark.AstTools.merge_atts_in_node(&1, class: "class4")
    ...(7)> add_class5 = &Earmark.AstTools.merge_atts_in_node(&1, class: "class5")
    ...(7)> add_class6 = &Earmark.AstTools.merge_atts_in_node(&1, class: "class6")
    ...(7)> tsp = Earmark.TagSpecificProcessors.new([{"a", add_class5}, {"b", add_class5}])
    ...(7)> m = Earmark.Options.make_options!(
    ...(7)>       postprocessor: add_class4,
    ...(7)>       registered_processors: [tsp, add_class6])
    ...(7)> |> make_postprocessor()
    ...(7)> [{"a", [], nil, nil}, {"c", [], nil, nil}, {"b", [], nil, nil}]
    ...(7)> |> Enum.map(m)
    [{"a", [{"class", "class6 class5 class4"}], nil, nil}, {"c", [{"class", "class6 class4"}], nil, nil}, {"b", [{"class", "class6 class5 class4"}], nil, nil}]
```

Of course the mechanics shown above is hidden if all we want is to trigger the postprocessor chain in `Earmark.as_html`, here goes a typical
example

```elixir
    iex(8)> add_target = fn node -> # This will only be applied to nodes as it will become a TagSpecificProcessors
    ...(8)>   if Regex.match?(~r{\.x\.com\z}, Earmark.AstTools.find_att_in_node(node, "href", "")), do:
    ...(8)>     Earmark.AstTools.merge_atts_in_node(node, target: "_blank"), else: node end
    ...(8)> options = [
    ...(8)> registered_processors: [{"a", add_target}, {"p", &Earmark.AstTools.merge_atts_in_node(&1, class: "example")}]]
    ...(8)> markdown = [
    ...(8)>   "http://hello.x.com",
    ...(8)>   "",
    ...(8)>   "[some](url)",
    ...(8)>  ]
    ...(8)> Earmark.as_html!(markdown, options)
    "<p class=\"example\">\n<a href=\"http://hello.x.com\" target=\"_blank\">http://hello.x.com</a></p>\n<p class=\"example\">\n<a href=\"url\">some</a></p>\n"
```

##### Use case: Modification of Link Attributes depending on the URL

This would be done as follows

```elixir
        Earmark.as_html!(markdown, registered_processors: {"a", my_function_that_is_invoked_only_with_a_nodes})
```

##### Use case: Modification of the AST according to Annotations

**N.B.** Annotation are an _experimental_ feature in 1.4.16-pre and are documented [here](https://github.com/RobertDober/earmark_parser/#annotations)

By annotating our markdown source we can then influence the rendering. In this example we will just
add some decoration

```elixir
    iex(9)> markdown = [ "A joke %% smile", "", "Charming %% in_love" ]
    ...(9)> add_smiley = fn {_, _, _, meta} = quad, _acc ->
    ...(9)>                case Map.get(meta, :annotation) do
    ...(9)>                  "%% smile"   -> {quad, "\u1F601"}
    ...(9)>                  "%% in_love" -> {quad, "\u1F60d"}
    ...(9)>                  _            -> {quad, nil}
    ...(9)>                end
    ...(9)>                text, nil -> {text, nil}
    ...(9)>                text, ann -> {"#{text} #{ann}", nil}
    ...(9)>              end
    ...(9)> Earmark.as_ast!(markdown, annotations: "%%") |> Earmark.Transform.map_ast_with(nil, add_smiley) |> Earmark.transform
    "<p>\nA joke  ὠ1</p>\n<p>\nCharming  ὠd</p>\n"
```

## Contributing

Pull Requests are happily accepted.

Please be aware of one _caveat_ when correcting/improving `README.md`.

The `README.md` is generated by `Extractly` as mentioned above and therefore contributors shall not modify it directly, but
`README.md.eex` and the imported docs instead.

Thank you all who have already helped with Earmark, your names are duly noted in [RELEASE.md](RELEASE.md).

## Author

Copyright © 2014,5,6,7,8,9, 2020,1 Dave Thomas, The Pragmatic Programmers & Robert Dober
@/+pragdave,  dave@pragprog.com & robert.dober@gmail.com

# LICENSE

Same as Elixir, which is Apache License v2.0. Please refer to [LICENSE](LICENSE) for details.

<!-- SPDX-License-Identifier: Apache-2.0 -->
