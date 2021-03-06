# How to add messages

## Required infos
- **title** - *required* Object in different languages (can be automatically translated from English with Gulp)
- **content** - *required* Object in different languages (can be automatically translated from English with Gulp)
- **id** - *required* If there are two identical IDs, ONLY the first message is displayed where the conditions apply.
- **created** - *required* Creation date in the format 2019-01-01T00:00:00.000Z

## Display options
- **class** - (default: info) Value can be info (blue), success (green), warning (yellow) and danger (red)
- **fa-icon** - (default: exclamation-triangle) Icon to be displayed on the left side [icons list](https://fontawesome.com/v4.7.0/icons/)

## Conditions
- **date-start** - When should the message be displayed (in format 2019-01-01T00:00:00.000Z)
- **date-end** - When should the message no longer be displayed (in format 2019-01-01T00:00:00.000Z)
- **conditions** - Object in format ("adapter" : "condition") -> All conditions are linked with "and"
  - **installed** - Adapter is installed (example: "iot": "installed")
  - **!installed** - Adapter is not installed  (example: "cloud": "!installed")
  - **bigger(x.x.x)** - Adapter version is bigger as (example: "admin": "bigger(2.2.2)")
  - **smaller(x.x.x)** - Adapter version is smaller than (example: "fronius": "smaller(1.2.2)")
  - **equals(x.x.x)** - Adapter has exactly the same version (example: "cloud": "equals(0.2.2)")
  - **between(x.x.x,y.y.y)** - The version of the adapter is between x and y or equal to x or y (example: "tankerkoenig": "between(1.0.5,2.0.4)") - only when 1.3.x is stable
