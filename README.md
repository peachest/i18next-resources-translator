# i18next-resources-translator

![License](https://img.shields.io/github/license/peachest/i18next-resources-translator)![Top Language](https://img.shields.io/github/languages/top/peachest/i18next-resources-translator)![GitHub go.mod Go version](https://img.shields.io/github/go-mod/go-version/peahcest/i18next-resources-translator)![Code Size](https://img.shields.io/github/languages/code-size/peachest/i18next-resources-translator)

![GitHub issues](https://img.shields.io/github/issues/peachest/i18next-resources-translator)![Github pull requests](https://img.shields.io/github/issues-pr/peachest/i18next-resources-translator)![GitHub last commit](https://img.shields.io/github/last-commit/peachest/i18next-resources-translator)![GitHub Release](https://img.shields.io/github/v/release/peachest/i18next-resources-translator)![Github Downloads](https://img.shields.io/github/downloads/peachest/i18next-resources-translator/total?label=github%20downloads)



  <p align="center">
    A translator based on Chat Nio for i18next resource files
    <br />
    <br />
    <a href="#quick-start">Quick Start</a>
    ·
    <a href="https://github.com/peachest/i18next-resources-translator/issues">Report Bug</a>
    ·
    <a href="https://github.com/peachest/i18next-resources-translator/issues">Propose Feature</a>
  </p>



- [Why](#Why)
- [Features](#Features)
- [Installation](#Installation)
- [Quick Start](#Quick Start)
- [Commands](#Commands)
  - [init](#init)
  - [compile](#compile)
- [Configuration](#Configuration)
- [License](#License)



## Why

When using the 18next, it can be quite cumbersome to maintain separate translation resources for each language.

Automating the translation of a single language's resources into files for other languages would greatly facilitate the process and save your time.



## Features

* Translation based on project [Chat Nio (Github)](https://github.com/Deeptrain-Community/chatnio), a powerful and beautiful **AI Aggregation** chat platform. Please check website [Chat Nio](https://chatnio.net/).

* Multiple translation mode

    * `all`: translate all value
    * `append`: translate appened value, but not deleted or changed
    * `update`: translate updated value, including newly appened, changed or deleted value.

<p align="right">(<a href="#i18next-resources-translator">back to top</a>)</p>

## Installation

1. Download a release from [Github Releases](https://github.com/peachest/i18next-resources-translator/releases) Page.
2. Drop into an empty directory
3. Add executable to your PATH

<p align="right">(<a href="#i18next-resources-translator">back to top</a>)</p>

## Quick Start

Create a new directory such as `./locale` to store i18next resource files. Here's an example of the directory structure

```sh
locale
└── en
    ├── namespace1.json
    └── namespace2.json
```

Initial translation config. This will create a `.i18next-resources-translator/config.json` inside `./locale` dir.

```sh
cd ./locale
i18nrt init --apiKey="" --srcLang="en" --targetLangs="zh"
```

Execute compile command inside `./locale` dir

```sh
i18nrt compile --model "gpt-3.6-turbo-16k" --mode "update"
```

And this will create resources for zh language.

```sh
locale
├── en
│   ├── namespace1.json
│   └── namespace2.json
└── zh
    ├── namespace1.json
    └── namespace2.json
```

<p align="right">(<a href="#i18next-resources-translator">back to top</a>)</p>

##  Commands

### init

Initial translation configuration. All flags is optional and will override that in config file.

```sh
i18nrt init
```



### compile

Start translating resources. All flags is optional and will override that in config file.

```sh
i18nrt compile 
```

<p align="right">(<a href="#i18next-resources-translator">back to top</a>)</p>

## Configuration

Flags in command line will override settings in config file.

```json
{
    // your Chat Nio API Key
    "apiKey": "",
    
    // ai model used for translating
    "model": "gpt-3.5-turbo",

    // prompt for ai model. use handlebar for templates
    "prompt": "Translate the following content form {{ srcLang }} to {{ targetLang }}. {{ content }}",
    
    // source language
    "srcLang": "",
    
    // target language list
    "targetLangs": [],
	
    // translation mode
    // all: translate all value.
    // append: translate appened value, without deleting or updating.
    // update: translate updated value, including newly appened, changed or deleted value. Default
    "mode": "update"
}
```

<p align="right">(<a href="#i18next-resources-translator">back to top</a>)</p>

## License

i18next-resources-translator is available under the GPL-3.0 license. See the [LICENSE](./LICENSE) file for more infomation.

