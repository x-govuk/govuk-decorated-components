# GOV.UK Decorated Components · [![test](https://github.com/x-govuk/govuk-decorated-components/actions/workflows/test.yml/badge.svg)](https://github.com/x-govuk/govuk-decorated-components/actions/workflows/test.yml)

Form components for the GOV.UK Design System that require less parameters to collect data. [Replace the multiple parameters needed for saving data with a single `decorate` parameter](https://x-govuk.github.io/govuk-prototype-rig/using-data/form-components/).

## Requirements

Node.js v16 or later.

## Installation

> **Note** These components are included by default with the [GOV.UK Prototype Rig](https://x-govuk.github.io/govuk-prototype-rig/).

```shell
npm install govuk-decorated-components --save
```

## Usage

To add them to the GOV.UK Prototype Kit, follow these steps:

1. Add `/node_modules/govuk-decorated-components` to your application’s views (`appViews`) in `server.js`:

    ```diff
      // Set up App
      var appViews = extensions.getAppViews([
    +   path.join(projectDir, '/node_modules/govuk-decorated-components'),
        path.join(projectDir, '/app/views/'),
        path.join(projectDir, '/lib/')
      ])
    ```

2. Add the `decorate` global function to your Nunjucks environment (`nunjucksAppEnv`) in `server.js`:

    ```diff
      var nunjucksAppEnv = nunjucks.configure(appViews, nunjucksConfig)

      // Add Nunjucks Globals
    + const { decorate } = require('govuk-decorated-components')
    + nunjucksAppEnv.addGlobal('decorate', decorate)

      // Add Nunjucks filters
      utils.addNunjucksFilters(nunjucksAppEnv)
    ```

3. Replace imported GOV.UK Frontend macros with those provided by this package:

    ```diff
    - {% from "govuk/components/button/macro.njk" import govukButton %}
    + {% from "x-govuk/decorated/button/macro.njk" import govukButton with context %}
    - {% from "govuk/components/character-count/macro.njk" import govukCharacterCount %}
    + {% from "x-govuk/decorated/character-count/macro.njk" import govukCharacterCount with context %}
    - {% from "govuk/components/checkboxes/macro.njk" import govukCheckboxes %}
    + {% from "x-govuk/decorated/checkboxes/macro.njk" import govukCheckboxes with context %}
    - {% from "govuk/components/date-input/macro.njk" import govukDateInput %}
    + {% from "x-govuk/decorated/date-input/macro.njk" import govukDateInput with context %}
    - {% from "govuk/components/file-upload/macro.njk" import govukFileUpload %}
    + {% from "x-govuk/decorated/file-upload/macro.njk" import govukFileUpload with context %}
    - {% from "govuk/components/input/macro.njk" import govukInput %}
    + {% from "x-govuk/decorated/input/macro.njk" import govukInput with context %}
    - {% from "govuk/components/radios/macro.njk" import govukRadios %}
    + {% from "x-govuk/decorated/radios/macro.njk" import govukRadios with context %}
    - {% from "govuk/components/select/macro.njk" import govukSelect %}
    + {% from "x-govuk/decorated/select/macro.njk" import govukSelect with context %}
    - {% from "govuk/components/textarea/macro.njk" import govukTextarea %}
    + {% from "x-govuk/decorated/textarea/macro.njk" import govukTextarea with context %}
    ```
