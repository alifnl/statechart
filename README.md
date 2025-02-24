This library can be used to emulate state chart without super long if else and make you confused in your project.

This is the example how this library should be used.

```C
state_chart ui_chart;

void function(){
  //a code to capture event, can be button event or other event from other function
  int menu_button_logic = read_event();



  /* event transistion = transition is state changes from 1 to other state
     transition is temporary and will be lost if not captured

     transition is triggered by event such as button, i.e menu button
  */
  if(ui_chart.event_trans(menu_button_logic == 1, STATE1, STATE2)){
    //change to STATE2
    //do something in your code
  }
  if(ui_chart.even_trans(menu_button_logic == 1, STATE2, STATE1){
    //change to STATE1
    //do something in your code
  }

  // you don't need to change the state by yourself, the library will do it for you. 
  if(ui_chart.is_state(STATE1)){
    //execute task if state is STATE1
  }
  if(ui_chart.is_state(STATE2)){
    //execute task if state is STATE2
  }

  //you need to reset the transition variable so transition would be executed once 
  ui_chart.reset_transition();
}
```

the even_trans() function will accept 3 arguments, the first is logic.
If the logic is true, then the state will change from first state (second argument) to next state (third argument).

You don't need to change state such as
```C
state = STATE1
```

the library will do it for you, you only need to define what to do in transition or in state.

Feel free to ask me.
