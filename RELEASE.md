
- [Nice addition to `Earmark.Transform.transform` to allow modification of the content of an AST node](https://github.com/pragdave/earmark/pr/443)

  Kudos to [Phillipp Tessenow](https://github.com/tessi)

## 1.4.20 2022-01-08

- Fix EarmarkParser version to 1.4.18 as the 1.4.x branch is not supporting Earmark anymore (1.5 should hopefully)

## 1.4.19 2021-12-04

This release is updating to `EarmarkParser` v1.4.18 with these [RELEASE NOTES](https://github.com/RobertDober/earmark_parser/blob/v1.14.8/RELEASE.md)

## 1.4.18 2021-10-30

- [Remove SmartyPants option for Parser](https://github.com/robertdober/earmark_parser/issues/438)

- Updated dependency to [EarmarkParser v1.4.17](https://github.com/RobertDober/earmark_parser/blob/v1.4.17/RELEASE.md)

## 1.4.17 2021-10-27

- [436 Better EEx integration into CLI with recursive includes of markdown files](https://github.com/pragdave/earmark/pull/436)

- [429 Illegal CLI option loops escript](https://github.com/pragdave/earmark/issues/429)

- [427 Bad docstring for Elixir < 1.12](https://github.com/pragdave/earmark/issues/427)

- [424-compiler-warning-about-eex](https://github.com/pragdave/earmark/issues/424)

- [406-Unexpected Newline in compact output](https://github.com/pragdave/earmark/issues/406)

# 1.4.16 2021-10-07

- [updates to EarmarkParser v1.4.16](https://github.com/RobertDober/earmark_parser/blob/v1.4.16/RELEASE.md)

- [`inner_html: true` allows to get rid of the enclosing `<p>` which is most useful when including `Earmark.as_htm!` into other markdown or HTML](https://github.com/pragdave/earmark/issues/418)

- [Test Coverage](https://github.com/pragdave/earmark/issues/414)

- [Refactoring of `Options`](https://github.com/pragdave/earmark/issues/412)

- [Refactoring of CLI code → Readability and Testability](https://github.com/pragdave/earmark/issues/411)

- [Allow using `.eex` templates as source](https://github.com/pragdave/earmark/issues/410)

- [Configuration of Link Attributes](https://github.com/pragdave/earmark/issues/407)


# 1.4.15 2021-04-18

- Pushed `EarmarkParser` dependency to version >= 1.4.13 which fixes a bug wich could crash the parser
    [IAL on ListItem can crash Parser](https://github.com/RobertDober/earmark_parser/issues/36)

- [404-assure-a-proplist-is-in-use-for-retrieval-of-filename](https://github.com/pragdave/earmark/pull/404)
  Kudos to [Manuel Rubio](https://github.com/manuel-rubio)

# 1.4.14 2021-02-21

- general improvments of the documentation

- removing duplicate documentation (`EarmarkParser`'s sdoc)

- moving from handmade implementation of doc generation to [Extractly](https://hex.pm/packages/extractly)

- fixing picture links in README.eex

- [403-warn-if-illegal-keyword-options-are-provided](https://github.com/pragdave/earmark/issues/403)

- [401-option-to-disable-html-escapes](https://github.com/pragdave/earmark/pull/401)
    Kudos to [paradox460](https://github.com/paradox460)

- [398-walk-ast-helper-and-ast-postprocessing-option](https://github.com/pragdave/earmark/issues/398)

- [397-typo fix](https://github.com/pragdave/earmark/pull/397)
    Kudos to [rubysolo](https://github.com/rubysolo)

# 1.4.13   2020-12-03

- A minor fix for the compact output option , Noo Issue, OMG ;)

# 1.4.12   2020-11-27

Adapted the CLI to accept the wikilinks switch for `EarmarkParser`

# 1.4.11   2020-11-26

- [394-compact-html-output](https://github.com/pragdave/earmark/pull/394)
    Kudos and Спасибо to [rinpatch](https://github.com/rinpatch)

- [387-treat-del-tag-as-compact-tag](https://github.com/pragdave/earmark/pull/387)
    Kudos to [Médi-Rémi Hashim](https://github.com/mediremi)

- [383-smartyants-inside-code-blocks](https://github.com/pragdave/earmark/issues/-)
    Kudos to [David Bernheisel](https://github.com/dbernheisel)

# 1.4.10 2020-07-18


- [381-deprecate-earmark-as-ast-usage](https://github.com/pragdave/earmark/issues/381)

- [373-markdown-in-footnotes](https://github.com/pragdave/earmark/issues/373)
    fixed in [`EarmarkParser`](https://github.com/robertdober/earmark_parser) v1.4.10

- [334-missing-space-btw-links](https://github.com/pragdave/earmark/issues/334-missing-space-btw-links)
    fixed in [`EarmarkParser`](https://github.com/robertdober/earmark_parser) v1.4.10

- [378-use-spdx-in-hex](https://github.com/pragdave/earmark/issues/378)
    Kudos to [Chulki Lee](https://github.com/chulkilee)

- [376-remove-application/0-from-mix.exs](https://github.com/pragdave/earmark/issues/376)
      Kudos to [Wojtek Mach](https://github.com/wojtekmach)

# 1.4.9 2020/07/02

- [375-earmark_parser-missing-in-application](https://github.com/pragdave/earmark/issues/375)

# 1.4.8 2020/07/01

This is a featureless release.

Its lone purpose is the extraction of all parsing and ast releated code into [EarmarkParser](https://hex.pm/packages/earmark_parser).

As it is feature identical to 1.4.7 downgrading in case of problems will be painless.

# 1.4.7 2020/06/29

- [371-still-spurious-ws-after-inline-tags](https://github.com/pragdave/earmark/issues/371)

# 1.4.6 2020/06/28

- [350-some-complicated-autolinks-cut](https://github.com/pragdave/earmark/issues/350)

- [359-unexpected-ws-in-html](https://github.com/pragdave/earmark/issues/359)

- [337-quadruple-ast-format](https://github.com/pragdave/earmark/issues/337)

- [366-simplify-transform](https://github.com/pragdave/earmark/issues/366)
    Kudos to [Eksperimental](https://github.com/eksperimental)

- [353-oneline-html-tags](https://github.com/pragdave/earmark/issues/353)

- [351-html-tags-without-newlines](https://github.com/pragdave/earmark/issues/351)

- [335-content-inside-table-cells-reversed](https://github.com/pragdave/earmark/issues/335)

- [348-no-crashes-for-invalid-URIs](https://github.com/pragdave/earmark/issues/348)
    Kudos to José Valim

- [347-dialyxir-errors](https://github.com/pragdave/earmark/issues/347)
    Fixed some of them, alas not all

# 1.4.5 2020/06/06

This is mostly a bugfix release, as there were edge cases that resulted in
Earmark crashing, notably

  - Bare IAL
  - unquoted attributes in html tags

Also autolinks (GFM extension) delivered incorrect URLS where parenthesis were involved,
for better GFM compatibility we therefore

  - Fixed broken parenthesis links (99% of all cases)
  - introduced the same URL encoding/decoding in links and link names of autolinks as GFM does

And last but not least all numeric options in the CLI can now be written with
underlines for readability.

- [343-error-parsing-unquoted-atts](https://github.com/pragdave/earmark/issues/343)

- [342 parens in pure links](https://github.com/pragdave/earmark/issues/342)

- [340 IAL might cause error](https://github.com/pragdave/earmark/issues/340)

- [339 Typos fix](ihttps://github.com/pragdave/earmark/pull/339)
    Kudos to [Ondrej Pinka](https://github.com/onpikono)

- [336 Smartypants: Convert three hyphens to em dash](https://github.com/pragdave/earmark/pull/336)
    Kudos to [Jony Stoten](https://github.com/jonnystoten)

- [324 Fix AST for links with nested elements](https://github.com/pragdave/earmark/pull/324)
    Kudos to [Wojtek Mach](https://github.com/wojtekmach)

- [320 Nested Blockquotes](https://github.com/pragdave/earmark/issues/320)

# 1.4.4 2020/05/01

- [338  Deprecation warnings in mixfile removed](https://github.com/pragdave/earmark/issues/338)

# 1.4.3 2019/11/23

- [309 fenced code allows for more than 3 backticks/tildes now](https://github.com/pragdave/earmark/issues/309)

- [302 Earmark.version returned a charlist, now a string](https://github.com/pragdave/earmark/issues/302)

- [298 Blockquotes nested in lists only work with an indentation of 2 spaces](https://github.com/pragdave/earmark/issues/298)


# 1.4.2 2019/10/14

- [296 code for tasks removed from package](https://github.com/pragdave/earmark/issues/296)
    The additional tasks are only needed for dev and have been removed from the hex package. **Finally**
- [PR#293 Nice fix for broken TOC links in README](https://github.com/pragdave/earmark/pull/293)
  Kudos to Ray Gesualdo [raygesualdo](https://github.com/raygesualdo)
- [291 Transformer whitespace inside / around &lt;code> &lt;pre> tags](https://github.com/pragdave/earmark/issues/291)
    The spurious whitespace has been removed
- [289 HTML Problem](https://github.com/pragdave/earmark/issues/289)
    The AST parser can now correctly distinguish between _generated_ AST (from md) and _parsed_ AST (from HTML)
- [288 Metadata allowed to be added to the AST](https://github.com/pragdave/earmark/issues/288)
    The default HTML Transformer ignores metadata in the form of a map with the exception of `%{meta: ...}`

# 1.4.1 2019/09/24

- [282 Always create a `<tbody>` in tables](https://github.com/pragdave/earmark/issues/282)
    Although strictly speaking a `<tbody>` is only needed when there is a `<thead>`, semantic
    HTML suggests the presence of `<tbody>` anyway.

- [281 Urls in links were URL endoded, that is actually a bug ](https://github.com/pragdave/earmark/issues/281)
    It is the markdown author's responsability to url encode her urls, if she does so correctly
    we double encoded the url before this fix.

- [279 Languages in code blocks were limited to alphanum names, thus excluding, e.g. C# ](https://github.com/pragdave/earmark/issues/279)

- [278 Implementing better GFM Table support ](https://github.com/pragdave/earmark/issues/278)
  Because of compatility issues we use a new option `gfm_tables` defaulting to `false` for this.
  Using this option `Earmark` will implement its own table extension **+** GFM tables at the same
  time.

- [277 Expose an AST to HTML Transformer](https://github.com/pragdave/earmark/issues/277)
  While it should be faster to call `to_ast|>transform` it cannot be used instead of `as_html` yet
  as the API is not yet stable and some subtle differences in the output need to be addressed.


# 1.4.0 2019/09/05

- [145 Expose AST for output manipulation]( https://github.com/pragdave/earmark/issues/145)

- [238 Pure Links are default now]( https://github.com/pragdave/earmark/issues/238)

- [256 Align needed Elixir Version with ex_doc (>= 1.7)]( https://github.com/pragdave/earmark/issues/256)

- [259 Deprecated option `sanitize` removed]( https://github.com/pragdave/earmark/issues/259)

- [261 Deprecated Plugins removed]( https://github.com/pragdave/earmark/issues/261)

- [265 Make deprecated `Earmark.parse/2` private]( https://github.com/pragdave/earmark/issues/265)


# 1.3.6 2019/08/30

Hopefully the last patch release of 1.3 before the structural changes of 1.4.

-  [#270]( https://github.com/pragdave/earmark/issues/270)
      Error messages during parsing of table celles were duplicated in a number, exponential to the number of table cells.

-  [#268]( https://github.com/pragdave/earmark/issues/268)
      Deprecation warnings concerning pure links showed fixed link to https://github.com/pragdave/earmark, at least a reasonable choice ;),
      instead of the text of the link.

-  [#266]( https://github.com/pragdave/earmark/issues/266)
    According to HTML5 Style Guide better XHTML compatibility by closing void tags e.g. `<hr>` --&gt; `<hr />`


# 1.3.5 2019/08/01

-  [#264]( https://github.com/pragdave/earmark/issues/264)
      Expose `Earmark.parse/2` but deprecate it.

-  [#262]( https://github.com/pragdave/earmark/issues/262)
    Remove non XHTML tags <colgroup> and <col>


-  [#236]( https://github.com/pragdave/earmark/issues/236)
      Deprecation of plugins.

-  [#257]( https://github.com/pragdave/earmark/issues/257)
      Deprecation of `sanitize` option.

# 1.3.4 2019/07/29


- [#254 pure links inside links](https://github.com/pragdave/earmark/issues/254)

# 1.3.3 2019/07/23

## Bugs
- [#240 code blocks in lists](https://github.com/pragdave/earmark/issues/240)
    Bad reindentation inside list items led to code blocks not being verabtim =&rt; Badly formatted hexdoc for Earmark

- [#243 errors in unicode link names](https://github.com/pragdave/earmark/issues/243)
    Regexpression was not UTF, thus some links were not correctly parsed
    Fixed in PR [244](https://github.com/pragdave/earmark/pull/244)
    Thank you [Stéphane ROBINO](https://github.com/StephaneRob)

## Features

- [#158 some pure links implemented](https://github.com/pragdave/earmark/issues/158)
    This GFM like behavior is more and more expected, I will issue a PR for `ex_doc` on this as discussed with
    [José Valim](https://github.com/josevalim)
    Deprecation Warnings are issued by default, but will be supressed for `ex_doc` in said PR.

-  Minor improvements on documentation
    In PR [235](https://github.com/pragdave/earmark/pull/235)
    Thank you - [Jason Axelson](https://github.com/axelson)

## Other

- Refactoring c.f. PR [246](https://github.com/pragdave/earmark/pull/246)
- Added Elixir version 1.9.0 for Travis c.f. PR #248

## Minor improvements on documentation

## PRs


  - [244](https://github.com/pragdave/earmark/pull/244)
  - [235](https://github.com/pragdave/earmark/pull/235)

## Kudos:

  - [Jason Axelson](https://github.com/axelson)
  - [Stéphane ROBINO](https://github.com/StephaneRob)


# 1.3.2 2019/03/23

* Fix for issues

  - [#224 titles might be extracted from outside link]( https://github.com/pragdave/earmark/issues/224 )
  - [#220 render only first link title always correctly]( https://github.com/pragdave/earmark/issues/220 )
  - [#218 replaced iff with longer but clearer if and only if ]( https://github.com/pragdave/earmark/issues/218 )

## Kudos:
  [niku](https://github.com/niku) for #218
  [Rich Morin](https://github.com/RichMorin) for #220 &amp; #224 as well as discussions

# 1.3.1 2018/12/21

  - [#212 spaces at line end force line break]( https://github.com/pragdave/earmark/issues/212 )
  - [#211 documentation explaining error messages]( https://github.com/pragdave/earmark/issues/211 )

# 1.3.0 2018/11/15

* Fix for issues
  - [#208 Inline code made Commonmark compatible]( https://github.com/pragdave/earmark/issues/208 )
  - [#203 escript does not report filename in error messages]( https://github.com/pragdave/earmark/issues/203 )
  - [#90 Parsing "...' or '..." as link titles removed]( https://github.com/pragdave/earmark/issues/90 )

## Dev dependencies updated

* credo -> 0.10

# 1.2.7 Not released Milestone merged into 1.3

  Special KUDOS for [pareehonos](https://github.com/pareeohnos) for a huge PR concerning the major Feature Request [#145](https://github.com/pragdave/earmark/issues/145)

  This cannot be merged yet but certainly is a great contribution to our codebase.


# 1.2.6 2018/08/21

* Fix for issues
  - [#198 Escapes inside link texts are ignored]( https://github.com/pragdave/earmark/issues/198 )
  - [#197 README task broken in Elixir 1.7]( https://github.com/pragdave/earmark/issues/197 )
  - [#191 Allow configurable timeout for parallel map]( https://github.com/pragdave/earmark/issues/191 )
  - [#190 do not include generated src/*.erl in the package]( https://github.com/pragdave/earmark/issues/190 )

* [#195 incorrect HTML for inline code blocks and IAL specified classes](https://github.com/pragdave/earmark/issues/195) from [Benjamin Milde]( https://github.com/LostKobrakai )

# 1.2.5 2018/04/02

* Fix for issues
  - [#161]( https://github.com/pragdave/earmark/issues/161 )
  - [#168]( https://github.com/pragdave/earmark/issues/168 )
  - [#172]( https://github.com/pragdave/earmark/issues/172 )
  - [#175]( https://github.com/pragdave/earmark/issues/175 )
  - [#181]( https://github.com/pragdave/earmark/issues/181 )

* [#178](https://github.com/pragdave/earmark/pull/178) from [jwworth](https://github.com/jwworth)

## Kudos:
  [jwworth](https://github.com/jwworth)

# 1.2.4 2017/11/28

* Fix for issue
  - [#166]( https://github.com/pragdave/earmark/issues/166 )

* [PR160](https://github.com/pragdave/earmark/pull/160) from [simonwebdesign](https://github.com/simonewebdesign)
* [PR163](https://github.com/pragdave/earmark/pull/163) from [nscyclone](https://github.com/nscyclone)
* [PR164](https://github.com/pragdave/earmark/pull/164) from [joshsmith](https://github.com/joshsmith)
* [PR165](https://github.com/pragdave/earmark/pull/165) from [asummers](https://github.com/asummers)

## Kudos:
   [simonwebdesign](https://github.com/simonewebdesign), [nscyclone](https://github.com/nscyclone),
   [joshsmith](https://github.com/joshsmith),  [asummers](https://github.com/asummers)


# 1.2.3 2017/07/26

* [PR151](https://github.com/pragdave/earmark/pull/151) from [joshuawscott](https://github.com/joshuawscott)

* Fixes for issues
  - [#150](https://github.com/pragdave/earmark/issues/150)
  - [#147](https://github.com/pragdave/earmark/issues/147)

## Kudos:

   [joshuawscott](https://github.com/joshuawscott)

# 1.2.2 2017/05/11

* [PR #144](https://github.com/pragdave/earmark/pull/144) from [KronicDeth](https://github.com/KronicDeth)

## Kudos:

  [KronicDeth](https://github.com/KronicDeth)

# 1.2.1 2017/05/03

* [PR #136](https://github.com/pragdave/earmark/pull/136) from [chrisalley](https://github.com/chrisalley)

* Fixes for issues
  - [#139](https://github.com/pragdave/earmark/issues/139)

## Kudos:

  [chrisalley](https://github.com/chrisalley)

# 1.2 2017/03/10

*  [PR #130](https://github.com/pragdave/earmark/pull/130) from [eksperimental](https://github.com/eksperimental)
*  [PR #129](https://github.com/pragdave/earmark/pull/129) from [Alekx](https://github.com/alkx)
*  [PR #125](//https://github.com/pragdave/earmark/pull/125) from [vyachkonovalov](https://github.com/vyachkonovalov)

* Fixes for issues
  - #127
  - #131

## Kudos:

  [vyachkonovalov](https://github.com/vyachkonovalov), [Alekx](https://github.com/alkx), [eksperimental](https://github.com/eksperimental)

# 1.1.1 2017/02/03

* PR from Natronium pointing out issue #123

* Fixes for issues
  - #123

## Kudos:

  [Natronium](https://github.com/Natronium)

# 1.1.0 2017/01/22

* PR from Michael Pope
* PR from Pragdave
* PR from christopheradams
* PR from [AndrewDryga](https://github.com/AndrewDryga)

* Fixes for issues
  - #106
  - #110
  - #114

## Kudos:
  [AndrewDryga](https://github.com/AndrewDryga), [Christopher Adams](https://github.com/christopheradams),
  [Michael Pope](https://github.com/amorphid)


# 1.0.3 2016/11/02

* PR from TBK145 with some dead code elimination.
* Implementation of command line switches for the `earmark` executable. Now any `%Earmark.Options{}` key can be
  passed in.

* Fixes for issues
  - #99
  - #96
  - #95
  - #103

## Kudos:
  Thijs Klaver (TBK145)

# 1.0.2 2016/10/10

* PR from pdebelak with a fix of #55
* PR from jonnystorm with a fix for a special case in issue #85
* test coverage at 100%
* PR from michalmuskala
* Fixed remaining compiler warnings from 1.0.1 (Elixir 1.3)
* PR from pdebelak to fix a factual error in the README
* Fixes for issues
  - #55
  - #86
  - #88
  - #89
  - #93

## Kudos:
  Jonathan Storm (jonnystorm), Michal Muskala (michalmuskala) & Peter Debelak (pdebelak)

# 1.0.1  2016/06/07

* fixing issue #81 by pushing this updated Changelog.md :)
* PR from mschae fixing issue #80 broken hex package

## Kudos:
  Michael Schaefermeyer (mschae) & Tobias Pfeiffer (PragTob)

# 1.0.0  2016/06/07

* --version | -v switch for `earmark` escript.
* added security notice about XSS to docs thanks to remiq
* PR from alakra (issue #59) to allow Hypens and Unicode in fenced code block names
* PR from sntran to fix unsafe conditional variables from PR
* PR from riacataquian to use maps instead of dicts
* PR from gmile to remove duplicate tests
* PR from gmile to upgrade poison dependency
* PR from whatyouhide to fix warnings for Elixir 1.4 with additional help from milmazz
* Travis for 1.2.x and 1.3.1 as well as OTP 19
* Fixes for issues:
  - #61
  - #66
  - #70
  - #71
  - #72
  - #77
  - #78

## Kudos:
Remigiusz Jackowski (remiq), Angelo Lakra (alakra), Son Tran-Nguyen (sntran), Mike Kreuzer (mikekreuzer),
Ria Cataquian (riacataquian), Eugene Pirogov (gmile), Andrea Leopardi (whatyouhide) & Milton Mazzarri (milmazz)

# 0.2.1  2016/01/15

* Added 1.2 for Travis
* PR from mneudert to fix HTMLOneLine detection

## Kudos:

Marc Neudert (mneudert)


# 0.2.0  2015/12/28

* PR from eksperimental guaranteeing 100% HTML5
* PR from imbriaco to decouple parsing and html generation and whitespace removal
* Fixes for issues:
  - #40
  - #41
  - #43
  - #48
  - #50
  - #51
* Explicit LICENSE change to Apache 2.0 (#42)
* Loading of test support files only in test environment thanks to José Valim
* IO Capture done correctly thanks to whatyouhide
* Warning for Elixir 1.2 fixed by mschae

## Kudos:

Eksperimental (eksperimental), Mark Imbriaco (imbriaco), Andrea Leopardi(whatyouhide), José Valim &
Michael Schaefermeyer (mschae)

# 0.1.19 2015/10/27

* Fix | in implicit lists, and restructur the parse a little.
  Many thanks to Robert Dober

# 0.1.17 2015/05/18

* Add strikethrough support to the HTML renderer. Thanks to
  Michael Schaefermeyer (mschae)


# 0.1.16 2015/05/08

* Another fix from José, this time for & in code blocks.


# 0.1.15 2015/03/25

* Allow numbered lists to start anywhere in the first four columns.
  (This was previously allowed for unnumbered lists). Fixes #13.


# 0.1.14 2015/03/25

* Fixed a problem where a malformed text heading caused a crash.
  We now report what appears to be malformed Markdown and
  continue, processing the line as text. Fixes #17.


# 0.1.13 2015/01/31

* José fixed a bug in Regex that revealed a problem with some
  Earmark replacement strings. As he's a true gentleman, he then
  fixed Earmark.


# 0.1.11 2014/08/18

* Matthew Lyon contributed footnote support.

      the answer is clearly 42.[^fn-why] In this case
      we need to…

      [^fn-why]: 42 is the only two digit number with
                 the digits 4 and 2 that starts with a 4.

  For now, consider it experimental. For that reason, you have
  to enable it by passing the `footnotes: true` option.


# 0.1.10 2014/08/13

* The spec is ambiguous when it comes to setext headings. I assumed
  that they needed a blank line after them, but common practice says
  no. Changed the parser to treat them as headings if there's no
  blank.


# 0.1.9 2014/08/05

* Bug fix—extra blank lines could be appended to code blocks.
* Tidied up code block HTML


# 0.1.7 2014/07/26

* Block rendering is now performed in parallel


# 0.1.6 07/25/14

* Added support for Kramdown-style attribute annotators for all block
  elements, so you can write

        # Warning
        {: .red}

        Do not turn off the engine
        if you are at altitude.
        {: .boxed #warning spellcheck="true"}

  and generate

        <h1 class="red">Warning</h1>
        <p spellcheck="true" id="warning" class="boxed">Do not turn
        off the engine if you are at altitude.</p>


# 0.1.5 07/20/14

* Merged two performance improvements from José Valim
* Support escaping of pipes in tables, so

        a  |  b
        c  |  d \| e

  has two columns, not three.


# 0.1.4 07/14/14

* Allow list bullets to be indented, and deal with potential subsequent
  additional indentation of the body of an item.


# 0.1.3 07/14/14

* Added tasks to the Hex file list


# 0.1.2 07/14/14

* Add support for GFM tables


# 0.1.1 07/09/14

* Move readme generation task out of mix.exs and into tasks/
* Fix bug if setext heading started on first line


# 0.1.0 07/09/14

* Initial Release
