# coc-mcfunction

mcfunction language highlighting for [Conquer of Completion](https://github.com/neoclide/coc.nvim)

[![github-license-badge]](https://github.com/Arcensoth/language-mcfunction)
[![vscode-version-badge]](https://marketplace.visualstudio.com/items?itemName=arcensoth.language-mcfunction)
[![discord-chat-badge]](https://discord.gg/ZdxgcAD)

This project provides two types of grammars: the default,
    [version-agnostic grammar](#version-agnostic-grammar) (shown below),
    and WIP [version-specific grammars](#version-specific-grammars).

- [Install]
  - [Installing the VSCode extension]
  - [Installing the SublimeText package]
- [Features]
  - [Syntax highlighting]
  - [Custom block comments]
- [Configure]
  - [Configuring the version-agnostic grammar]
  - [Configuring the version-specific grammars]
- [Customize]
- [Contribute]
- [Resources]

[![Showcase](https://i.imgur.com/0agDB4B.png)](https://i.imgur.com/0agDB4B.png)

## Features

### Syntax highlighting

Here's an [album](https://imgur.com/a/a8LvRjK) with everything below.

- [x] [Comments and indentation](https://i.imgur.com/1N5zlkj.png):
    `# This is a comment`
- [x] [Custom block comments]:
    `#> This is a block heading`
- [x] [Booleans](https://i.imgur.com/FBKTc5u.png):
    `true` / `false`
- [x] [Numbers](https://i.imgur.com/KSvbapt.png):
    `20` / `3.14` / `.001`
- [x] [Operations](https://i.imgur.com/iYvND6j.png):
    `=` / `/=` / `%=` / etc
- [x] [Ranges](https://i.imgur.com/ZUicjD0.png):
    `1..` / `3.14..20` / `...001`
- [x] [Relative coordinates](https://i.imgur.com/3qaVlrO.png):
    `~` / `~10` / `~-4.5`
- [x] [Local coordinates](https://i.imgur.com/9De4utY.png):
    `^` / `^-1` / `^.05`
- [x] [Resource locations](https://i.imgur.com/wDWTzSw.png):
    `minecraft:chests/simple_dungeon` / `#minecraft:wools`
- [x] [Block predicates](https://i.imgur.com/7QpQsi6.png):
    `minecraft:dispenser[facing=up]`
- [x] [Unquoted strings](https://i.imgur.com/82vSj6Q.png):
    `mypack.some.tag` / `mypack.custom_crafting_marker`
- [x] [Quoted strings with escaping](https://i.imgur.com/3Ns8MzH.png):
    `"hello world"` / `"CustomName With Spaces"`
- [x] [Single-quoted strings](https://i.imgur.com/6BtgTvu.png):
    `'hello world'` / `'{"text": "hello world"}'`
- [x] [NBT compounds/lists](https://i.imgur.com/ISjyX3Z.png):
    `{ Fire: 20s , NoGravity: true, Tags: [ "mytag" ] }`
- [x] [NBT paths](https://i.imgur.com/DVPvepj.png):
    `SelectedItem.Count` / `RecordItem.tag.mycustomtag`
- [x] [JSON/text components](https://i.imgur.com/5cJVdhc.png):
    `{"text": "hello world", "color": "blue"}`
- [x] [UUIDs](https://i.imgur.com/uvwKnCC.png):
    `f7a39418-72ca-4bf2-bc7e-ba9df67a4707` `0-0-0-0-0`
- [x] [Fakeplayers](https://i.imgur.com/jNODt4g.png):
    `#hidden` / `$fakefoo` / `%fakebar`
- [x] [Base selectors](https://i.imgur.com/6eWmGa4.png):
    `@e`
- [x] [Selectors with arguments](https://i.imgur.com/Ut4W6pF.png):
    `@e[tag=foo]` / `@e[tag=!foo]`
  - [x] [Literal arguments](https://i.imgur.com/LtMfOGW.png):
      `gamemode` / `sort`
  - [x] [Numeric arguments](https://i.imgur.com/FvnxwYD.png):
      `x` / `y` / `z` / `limit`
  - [x] [Range arguments](https://i.imgur.com/DiLdNU6.png):
      `distance` / `level`
  - [x] [Resource location arguments](https://i.imgur.com/ZQ920Yw.png):
      `type`
  - [x] [Unquoted string arguments](https://i.imgur.com/svqzc2o.png):
      `tag`
  - [x] [Quoted string arguments](https://i.imgur.com/ahm8HYb.png):
      `name`
  - [x] [NBT compound arguments](https://i.imgur.com/JqWrpVm.png):
      `nbt`
  - [x] [Score arguments](https://i.imgur.com/L7f9wJ3.png):
      `scores`
  - [x] [Advancement arguments](https://i.imgur.com/yQj5Oye.png):
      `advancements`

### Custom block comments

It's common for datapack developers to comment parts of their code with things
    like headings, parameters, return values, etc. To support these patterns
    for those who wish to use them, the grammar implements custom block comments.
    These types of comments are gated behind
    a vanilla-compatible alternate comment style.

The prefix `#>` can be used to initiate a block comment:

```mcfunction
#> This is a block heading
# All adjacent comments will be considered part of the block.
#
# So long as you keep comments attached, they will remain part of the block.

# This line no longer attached to the block.

#> But we can start a new block here!
```

[Click here for a detailed example.](https://i.imgur.com/i2ojCZS.png)

As of writing there is no documentation standard,
    however the grammar has the capacity to support this
    via block comments and alternate comment styles.

## Configure

### Configuring the version-agnostic grammar

This is a generic "version-agnostic" grammar that does not target
    any particular version of Minecraft. As a result it may not be
    as accurate as version-specific grammars, however it will continue to work
    for multiple versions of the game.

The version-agnostic `mcfunction` language should be active by default.
    It provides a decent fallback for otherwise unsupported versions of Minecraft.
    In order to do this, it must not assume any particular version.
    Because it cannot assume a version, it cannot provide context-sensitive highlighting.

In the future, the [version-specific grammars] will be preferred when available.

### Configuring the version-specific grammars

> **The version-specific grammars are currently under heavy development.**
    These grammars are incomplete and experimental. They do not yet support
    the same feature set as the [version-agnostic grammar]. Please only use
    these grammars if you intend to contribute in some form,
    such as pull requests, bug reports, or general feedback.

The version-specific grammars are partially generated based on Minecraft's generated data, which is available for Minecraft versions 1.13 and higher. They have context-sensitive highlighting and command validation comparable to the in-game command bar.

In VSCode, you can easily choose which version of mcfunction to use by changing the `.mcfunction` extension association in your workspace settings:

```json
"files.associations": {
  "*.mcfunction": "mcfunction-snapshot"
}
```

This option can also be set on the user-level in `settings.json` or folder-level in `.vscode/settings.json`.

## Customize
Currently available for the [version-specific grammars].

Scopes have been assigned with user customization in mind. If your editor allows scope overrides, this will make it easy to customize your own colours for a variety of scopes.

- [Customizing errors]
- [Customizing comments]
- [Customizing commands]
- [Customizing selectors]
- [Customizing NBT]
- [Customizing text components]
- [Customizing resource locations]
- [Customizing strings]
- [Customizing numbers]
- [Customizing tags, teams, and objectives]
- [Other customizable scopes]

### Customizing errors
Short name  | Full scope name                           | Examples
----------- | ----------------------------------------- | ----------
`invalid`   | `invalid.illegal._.invalid.mcfunction`    | `execute (foo)`
`underline` | `markup.underline._.underline.mcfunction` | `execute (foo)`

### Customizing comments
Short name                        | Full scope name                                               | Examples
--------------------------------- | ------------------------------------------------------------- | ----------
`comment.plain`                   | `comment._.plain.comment.mcfunction`                          | `(# This is a plain comment)`
`comment.block`                   | `comment.block._.block.comment.mcfunction`                    | `(#> This is part of a block comment)`
`comment.block.symbol`            | `markup.list._.symbol.block.comment.mcfunction`               | `(#)> This is part of a block comment`
`comment.block.prefix`            | `markup.list._.prefix.block.comment.mcfunction`               | `#(>) This is part of a block comment`
`comment.block.heading_1`         | `markup.bold._.heading_1.block.comment.mcfunction`            | `#> (This is part of a block comment)`
`comment.block.heading_2`         | `markup.list._.heading_2.block.comment.mcfunction`            | `#> (This is part of a block comment)`
`comment.block.annotation.label`  | `markup.heading._.label.annotation.block.comment.mcfunction`  | `#> (@annotation) some annotation`
`comment.block.annotation.text`   | `comment.block._.text.annotation.block.comment.mcfunction`    | `#> @annotation (some annotation)`

### Customizing commands
Short name      | Full scope name                         | Examples
--------------- | --------------------------------------- | ----------
`command`       | `keyword.control._.command.mcfunction`  | `(execute) as @a run (function)`
`subcommand`    | `keyword.other._.subcommand.mcfunction` | `execute (as) @a (run) function`
`command.slash` | `keyword.control._.command.mcfunction`  | `/`

### Customizing selectors
Short name                | Full scope name                                               | Examples
------------------------- | ------------------------------------------------------------- | ----------
`target_selector.base`    | `support.class._.base.target_selector.mcfunction`             | `@a`
`target_selector.bracket` | `support.class._.bracket.target_selector.mcfunction`          | `[]`
`target_selector.equals`  | `support.class._.equals.target_selector.mcfunction`           | `=`
`target_selector.comma`   | `support.class._.comma.target_selector.mcfunction`            | `,`
`target_selector.not`     | `constant.character.escape._.not.target_selector.mcfunction`  | `!`
`target_selector.param`   | `keyword.other._.param.target_selector.mcfunction`            | `tag` / `type`
`score_map.bracket`       | `storage._.bracket.score_map.mcfunction`                      | `{}`
`score_map.equals`        | `storage._.equals.score_map.mcfunction`                       | `=`
`score_map.comma`         | `storage._.comma.score_map.mcfunction`                        | `,`
`advancement_map.bracket` | `storage._.bracket.advancement_map.mcfunction`                | `{}`
`advancement_map.equals`  | `storage._.equals.advancement_map.mcfunction`                 | `=`
`advancement_map.comma`   | `storage._.comma.advancement_map.mcfunction`                  | `,`

### Customizing NBT
Short name              | Full scope name                             | Examples
----------------------- | ------------------------------------------- | ----------
`nbt_compound.bracket`  | `storage._.bracket.nbt_compound.mcfunction` | `{}`
`nbt_compound.colon`    | `storage._.colon.nbt_compound.mcfunction`   | `:`
`nbt_compound.comma`    | `storage._.comma.nbt_compound.mcfunction`   | `,`
`nbt_list.bracket`      | `storage._.bracket.nbt_list.mcfunction`     | `[]`
`nbt_list.comma`        | `storage._.comma.nbt_list.mcfunction`       | `,`

### Customizing NBT paths
Short name                  | Full scope name                                   | Examples
--------------------------- | ------------------------------------------------- | ----------
`nbt_path.property`         | `string._.property.nbt_path.mcfunction`           | `(RecordItem)`
`nbt_path.dot`              | `storage._.dot.nbt_path.mcfunction`               | `RecordItem(.)tag`
`nbt_path.compound.bracket` | `storage._.bracket.compound.nbt_path.mcfunction`  | `SelectedItem({)(})`
`nbt_path.index.bracket`    | `storage._.bracket.index.nbt_path.mcfunction`     | `Inventory([)(])`

### Customizing text components
Short name                        | Full scope name                                       | Examples
--------------------------------- | ----------------------------------------------------- | ----------
`text_component.bracket`          | `storage._.bracket.text_component.mcfunction`         | `{}[]`
`text_component.colon`            | `storage._.colon.text_component.mcfunction`           | `:`
`text_component.comma`            | `storage._.comma.text_component.mcfunction`           | `,`
`text_component.property`         | `string._.property.text_component.mcfunction`         | `text` / `color` / `selector`
`text_component.property.color`   | `string._.color.property.text_component.mcfunction`   | `red` / `green` / `blue`
`text_component.property.keybind` | `string._.keybind.property.text_component.mcfunction` | `key.drop` / `key.use`
`text_component.property.event`   | `string._.event.property.text_component.mcfunction`   | `run_command` / `show_text`

### Customizing resource locations
Short name                            | Full scope name                                                         | Examples
------------------------------------- | ----------------------------------------------------------------------- | ----------
`resource_location.namespace`         | `entity.name.function._.namespace.resource_location.mcfunction`         | `(mypack):some/resource`
`resource_location.colon`             | `entity.name.function._.colon.resource_location.mcfunction`             | `mypack(:)some/resource`
`resource_location.path`              | `entity.name.function._.path.resource_location.mcfunction`              | `mypack:(some/resource)`
`tagged_resource_location.hash`       | `entity.name.function._.hash.tagged_resource_location.mcfunction`       | `(#)mypack:some/resource`
`tagged_resource_location.namespace`  | `entity.name.function._.namespace.tagged_resource_location.mcfunction`  | `#(mypack):some/resource`
`tagged_resource_location.colon`      | `entity.name.function._.colon.tagged_resource_location.mcfunction`      | `#mypack(:)some/resource`
`tagged_resource_location.path`       | `entity.name.function._.path.tagged_resource_location.mcfunction`       | `#mypack:(some/resource)`

### Customizing strings
Short name              | Full scope name                                         | Examples
----------------------- | ------------------------------------------------------- | ----------
`string`                | `string._.string.mcfunction`                            | `("hello world")`
`string_escape`         | `constant.character.escape._.string_escape.mcfunction`  | `"hello(\n)newline"`
`word`                  | `string._.word.mcfunction`                              | `foo` / `foo_bar`
`keyword`               | `keyword._.word.mcfunction`                             | `nearest` / `creative`

### Customizing numbers
Short name                    | Full scope name                                             | Examples
----------------------------- | ----------------------------------------------------------- | ----------
`number`                      | `constant.numeric._.number.mcfunction`                      | `0` / `123` / `-99`
`range.minimum`               | `constant.numeric._.minimum.range.mcfunction`               | `(10)..20`
`range.maximum`               | `constant.numeric._.maximum.range.mcfunction`               | `10..(20)`
`range.ellipsis`              | `keyword.control._.ellipsis.range.mcfunction`               | `10(..)20`
`position.absolute.number`    | `constant.numeric._.number.absolute.position.mcfunction`    | `(10) ~20 (30)`
`position.relative.operator`  | `keyword.control._.operator.relative.position.mcfunction`   | `10 (~)20 30`
`position.relative.number`    | `constant.numeric._.number.relative.position.mcfunction`    | `10 ~(20) 30`
`position.local.operator`     | `keyword.control._.operator.local.position.mcfunction`      | `(^)10 (^)20 (^)30`
`position.local.number`       | `constant.numeric._.number.local.position.mcfunction`       | `^(10) ^(20) ^(30)`

### Customizing tags, teams, and objectives
Short name                  | Full scope name                                                 | Examples
--------------------------- | --------------------------------------------------------------- | ----------
`entity_tag`                | `entity.other.attribute-name._.entity_tag.mcfunction`           | `mypack.some.tag`
`scoreboard_team `          | `entity.other.attribute-name._.scoreboard_team.mcfunction`      | `mypack.blue`
`scoreboard_objective`      | `entity.other.attribute-name._.scoreboard_objective.mcfunction` | `mypack.points`
`score_holder.all`          | `support.class._.all.score_holder.mcfunction`                   | `*`
`score_holder.fakeplayer `  | `support.class._.fakeplayer.score_holder.mcfunction`            | `#temp` / `$mypack.calc`

### Other customizable scopes
Short name                | Full scope name                               | Examples
------------------------- | --------------------------------------------- | ----------
`boolean`                 | `constant.numeric._.boolean.mcfunction`       | `true` / `false`
`entity_anchor`           | `constant.numeric._.entity_anchor.mcfunction` | `eyes` / `feet`
`swizzle`                 | `constant.numeric._.swizzle.mcfunction`       | `y` / `xz` / `xyz`
`target.uuid`             | `support.class._.uuid.target.mcfunction`      | `f7a39418-72ca-4bf2-bc7e-ba9df67a4707` / `0-0-0-0-0`
`target.player_name`      | `support.class._.uuid.target.mcfunction`      | `Arcensoth` / `some_guy`
`generic.dict.bracket`    | `storage._.bracket.dict.generic.mcfunction`   | `({) key: value (})`
`generic.dict.content`    | `string._.content.dict.generic.mcfunction`    | `{( key: value )}`
`generic.list.bracket`    | `storage._.bracket.list.generic.mcfunction`   | `([) item, item (])`
`generic.list.content`    | `string._.content.list.generic.mcfunction`    | `[( item, item )]`

## Contribute
[Contributions are welcome; see `CONTRIBUTING.md`.](./CONTRIBUTING.md)

## Resources
- https://github.com/Arcensoth/language-tmdemo
- https://github.com/github/linguist/blob/master/CONTRIBUTING.md
- https://github.com/github/linguist/blob/master/vendor/README.md
  - https://github.com/Microsoft/TypeScript-TmLanguage/blob/master/TypeScript.YAML-tmLanguage
- https://code.visualstudio.com/api/language-extensions/syntax-highlight-guide
- https://code.visualstudio.com/api/extension-guides/icon-theme
- https://gist.github.com/Aerijo/b8c82d647db783187804e86fa0a604a1
- https://macromates.com/manual/en/language_grammars
- https://regex101.com/

[github-license-badge]: https://img.shields.io/github/license/arcensoth/language-mcfunction.svg?logo=github
[vscode-version-badge]: https://img.shields.io/visual-studio-marketplace/v/arcensoth.language-mcfunction.svg?logo=visual-studio-code
[discord-chat-badge]: https://img.shields.io/discord/154777837382008833.svg?color=%237289DA&label=chat&logo=discord&logoColor=%23FFFFFF

[Install]: #install
[Installing the VSCode extension]: #installing-the-vscode-extension
[Installing the SublimeText package]: #installing-the-sublimetext-package
[Features]: #features
[Syntax highlighting]: #syntax-highlighting
[Custom block comments]: #custom-block-comments
[Configure]: #configure
[Configuring the version-agnostic grammar]: #configuring-the-version-agnostic-grammar
[version-agnostic grammar]: #configuring-the-version-agnostic-grammar
[Configuring the version-specific grammars]: #configuring-the-version-specific-grammars
[version-specific grammars]: #configuring-the-version-specific-grammars
[Customize]: #customize
[Customizing errors]: #customizing-errors
[Customizing comments]: #customizing-comments
[Customizing commands]: #customizing-commands
[Customizing selectors]: #customizing-selectors
[Customizing NBT]: #customizing-NBT
[Customizing text components]: #customizing-text-components
[Customizing resource locations]: #customizing-resource-locations
[Customizing strings]: #customizing-strings
[Customizing numbers]: #customizing-numbers
[Customizing tags, teams, and objectives]: #customizing-tags-teams-and-objectives
[Other customizable scopes]: #other-customizable-scopes
[Contribute]: #contribute
[Resources]: #resources
