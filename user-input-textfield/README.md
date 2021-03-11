# user-input-textfield

## About
Text field that has fancy css animations.

### How to install
Simply grab the vue component and import it.

## How to use it
### Size
```
<user-input-text-field width='200px' height='60px' />
```
#### Format
- px
- em
- rem
- %

### Color
```
#parentClass input:focus ~ label,
#parentClass input.inputIn ~ label{
  color: blue;
}

#parentClass input:hover,
#parentClass input:focus,
#parentClass input.inputIn{
  border-color: blue;
}
```

### Error
If you would like some error animation, simply bind a boolean value.
<br>
*Important: The boolean value need to get reset to false every form submission attempt.*
```
<user-input-text-field :error="error">

data(){
  return{
    error: false
  }
}
```

