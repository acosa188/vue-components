# user-input-textfield

## About
Text field that could be your regular text field, username field, email field, and password field. It takes care with error css magic and it could also returns a callback function if there is an error.

### How to install
Simply grab the vue component and import it.

## How to use it
### Size
```
<user-input-text-field width='200px' height='60px' />
```

### Color
```
#parentclass #user-text-field.mouseOver{
  border-color: #2e2c9b;
}
#parentclass label.focusIn,
#parentclass #user-text-field.mouseOver > i{
  color:#2e2c9b;
}
```

### Icons
*Note: icon names should be chosen using [bootstrsap icons](https://icons.getbootstrap.com/)*
```
<user-input-text-field icon="person-fill" />
```

