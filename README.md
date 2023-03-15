# Hugo Gravatar Module

[![Used By](https://img.shields.io/badge/dynamic/json?color=success&label=used+by&query=repositories_humanize&logo=hugo&style=flat-square&url=https://api.razonyang.com/v1/github/dependents/razonyang/hugo-mod-gravatar)](https://github.com/razonyang/hugo-mod-gravatar/network/dependents)
![Hugo Requirements](https://img.shields.io/badge/dynamic/json?color=important&label=requirements&query=requirements&logo=hugo&style=flat-square&url=https://api.razonyang.com/v1/hugo/modules/github.com/razonyang/hugo-mod-gravatar)
[![License](https://img.shields.io/github/license/razonyang/hugo-mod-gravatar?style=flat-square)](https://github.com/razonyang/hugo-mod-gravatar/blob/main/LICENSE)
[![Version](https://img.shields.io/github/v/tag/razonyang/hugo-mod-gravatar?label=version&style=flat-square)](https://github.com/razonyang/hugo-mod-gravatar/tags)

This module ships with several partials for [Gravatar](https://en.gravatar.com/).

## Installation

> Requires extended Hugo and Go.

Append the `github.com/razonyang/hugo-mod-gravatar` to the `theme`.

```toml
theme = [
    "github.com/razonyang/hugo-mod-gravatar"
]
```

## Site Parameters

> The following parameters can be overridden by [partials' parameters](#partials-parameters).

| Name | Type | Default | Description
|---|:-:|:-:|---
| `gravatar` | Object | - |
| `gravatar.default` | String | `mp` | The default image. Available options: `404`, `mp`, `identicon`, `monsterid`, `wavatar`, `retro`, `robohash`, `blank` or an image URL.
| `gravatar.forceDefault` | Boolean | `false` | Force the default image to always load.
| `gravatar.size` | Integer | `80` | Single pixel dimension, since the images are square.
| `gravatar.rating` | String | - | Available options: `g`, `pg`, `r` and `x`.
| `gravatar.className` | String | `gravatar-img` | The class name of img tag.

See [configuration](https://github.com/razonyang/hugo-mod-gravatar/blob/main/config.yml) and [Gravatar image request](https://en.gravatar.com/site/implement/images/) for details.

## Partials

| Partial | Description | Example
|---|---|---
| `gravatar/avatar` | renders a Gravatar image by a raw email address. | `{{ partial "gravatar/avatar" "user@example.com" }}`
| `gravatar/avatar-hash` | renders a Gravatar image by a MD5 encrypted email address hash. | `{{ partial "gravatar/avatar-hash" "e7501ec2b3cd95d6af8964743c1d27c7" }}`
| `gravatar/avatar-params` | allow specifying the default image, image size, rating and class name. | `{{ partial "gravatar/avatar-params" $params }}`, see [partials' parameters](#partials-parameters).
| `gravatar/avatar-url` | returns the Gravatar image URL instead of img tag. | `{{ partial "gravatar/avatar-url" $params }}`, see [partials' parameters](#partials-parameters).

You can find more examples on https://projects.razonyang.com/hugo-mod-gravatar/.

### Partials' Parameters

> The following parameters will override the global parameters if present.

| Name | Type | Description
|---|:-:|---
| `Id` | String | The MD5 encrypted email address hash, you **MUST** provide one of the `Id` or `Email`.
| `Email` | String | The raw email address.
| `Default` | String | The default image.
| `ForceDefault` | Boolean | Force the default image to always load.
| `Size` | Integer | The image size.
| `Rating` | String | The image rating.
| `ClassName` | String | The class name of img tag. Doesn't work with the `gravatar/avatar-url` partial.

```html
{{ $params := dict (
    "Id" "e7501ec2b3cd95d6af8964743c1d27c7"
    "Size" 120
    "Default" "monsterid"
    "ForceDefault" true
    "Rating" "x"
    "ClassName" "avatar-img-circle"
) }}
{{ partial "gravatar/avatar-params" $params }}
{{ partial "gravatar/avatar-url" $params }}
```
