# Fliplet Default Theme (Fliplet Theme)

To develop themes, please follow our [theme development guide](https://github.com/Fliplet/fliplet-cli).

---

Install dependencies:

```
$ npm install fliplet-cli -g
```

---

Clone and run for development:

```
$ git clone https://github.com/Fliplet/fliplet-theme-default.git
$ cd fliplet-theme-default

$ fliplet run
```

## Understanding theme.json structure
Fliplet themes are mainly SCSS files and a .json file that defines the variables to be used in the SCSS, and their default values.
Below is a quick description of the .json file:

`name`: Theme name  
`package`: A unique name that should have a prefix of `com.fliplet.`  
`version`: The version of the theme  
`icon`: The relative path to the icon image
`dependencies`: An array of package names
`assets`: An array of relative paths of the assets required to load the theme
`settings`: An object with the `configuration` array containing all the fields of the theme

## Understanding theme fields structure
```js
"configuration": [ // Array with the entire theme configuration
  {
    "name": "Primary button", // Name of the component or group of settings
    "packages": ["com.fliplet.primary-button"], // Use this key if the fields can be used to customize a Fliplet component
    "variables": [ // Array of all the fields in the group
      {
        "description": "Button", // The label name before the fields
        "fields": [ // Array of fields below the label
          {
            "name": "primaryButtonWidth", // Variable name used in the SCSS
            "default": "100%", // Default value
            "property": "%", // Defines the unit of the default value. This is only used in the field type 'size'
            "isFullRow": true, // Makes the field full width. The default is inline items
            "breakpoints": { // Object that defines the variables for Tablet and Desktop breakpoints
              "tablet": {
                "name": "primaryButtonWidthTablet", // Variable name used in the SCSS
                "default": "auto", // Default value
                "property": "px" // Defines the unit of the default value. This is only used in the field type "size"
              },
              "desktop": {
                "name": "primaryButtonWidthDesktop", // Variable name used in the SCSS
                "default": "inherit-tablet", // Default value
                "property": "px" // Defines the unit of the default value. This is only used in the field type "size"
              }
            },
            "type": "size", // The type of field. All types that we support: 'align', 'background', 'border-style', 'color', 'font', 'font-style', 'image', 'margin-align', 'select', 'size'
            "label": "Size", // Small label/description that appears next to the field
            "properties": ["px", "pt", "em", "rem", "%", "auto"] // Array of possible choices for a dropdown field. This is only available of the following fields: 'font-style', 'select', 'size'
          }
        ]
      }
    ]
  }
]
```

