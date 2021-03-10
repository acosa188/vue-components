# user-button

## About
Sign In or Sign Up button that got some fancy animation. Lazy to implement animation for each state of your button? Well my friend, here is your solution. A compact vue component for you to use.

### How to install
Simply grab the vue component and import it. Don't forget to add font-awesome. Refer to the requirement section.

## How to use it
### Size
```
<user-button height="50px" width="200px"/>
```
### Binding btn_state
Example below. More information about the button state can be found in the component states section.
```
<user-button :btn_state="buttonState">
data(){
    return(){
        buttonState: "standby"
    }
}
```
### Component states
There is a prop called btn_state: *String* that handles the animation base on what state the component is in.
- standby
- loading
- success
- error
### Requirements
Copy and paste this in the header section of index.html
```
<link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css" rel="stylesheet">
```

