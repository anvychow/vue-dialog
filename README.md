# VueDialog

Dialog windows for Vue (like confirm or alert), based on Vuedals.

These dialogs will return a _Promise_ when called that will resolve when confirmed and rejects when denied

It provides 3 types of dialogs:

- Alert
- Confirm
- Hard Confirm

More info about the types, below

## DEMO


## Example

```js
import { VueDialog } from 'vuedialog';

var vm = new Vue({
	el: '#app',
	
	components: {
        VueDialog
    },

    methods: {
        continue() {
            VueDialog.confirm('Are you sure of this?')
                .then(_ => alert('You are sure'))
                .catch(_ => alert('Phew..'));
        }
    },
	
	template: `<div>To continue, <span @click="continue()">click here</span></div>`
});
```

## Dependencies
This plugin depends on `Vuedals` so you need to have Vuedals as a component dependency if you don't:

```
$ npm install vuedals --save
```

```
import { Component as Vuedal } from 'vuedals';

Vue.component('my-component', {
    components: {
        Vuedal
    },

    template: `
        <div>
            <vuedal></vuedal>
        </div>
    `
});
```

For more info on how to setup Vuedals, check the repo: https://github.com/javisperez/vuedals/

## Install

```
$ npm install vuedialog --save
```

## Usage 
```
import { VueDialog } from 'vuedialog';

Vue.component('my-component', {
    methods: {
        myMethod() {
            VueDialog.alert('Watch me!', 'Ok, done!');
        }
    }
});
```

## Dialog types

This plugin has 3 methods you can call:

### alert

`VueDialog.alert(message[, buttonLabel])`

Will open an alert window with the given message.

##### arguments
| Argument           | Type         | Default     | Description                         |
|--------------------|--------------|-------------|-------------------------------------|
| **message**        | String       | ''          | The mesage to show                  |
| **buttonLabel**    | String       | 'Ok'        | The label of the button             |

### confirm

`VueDialog.confirm(message[, options])`

Will open a confirm window with the message and the given options.

##### arguments
| Argument            | Type         | Default          | Description                         |
|---------------------|--------------|------------------|-------------------------------------|
| **message**         | String       | 'Are you sure?'  | The mesage to show                  |
| **options**         | Object       | *see below*      | Options for this confirm            |

###### options
| Option    | Type   | Default                      | Description                                 |
|-----------|--------|------------------------------|---------------------------------------------|
| **title** | String | 'Please confirm'             | The title of the window                     |
| **labels**| Object | {ok: *'Ok'*, cancel: *'Cancel'*} | The labels of the \<ok\> and \<cancel\> buttons |

### hardConfirm

`VueDialog.hardConfirm(message[, confirmationMessage[, options]])`

Opens a "hard confirm" window dialog, this is a confirm in which the user has to type a given *confirmation message* and press the "im sure" button for a given amount of seconds. This is intended for really sensitive actions.

##### arguments
| Argument                 | Type         | Default                       | Description                            |
|--------------------------|--------------|-------------------------------|----------------------------------------|
| **message**              | String       | 'Are you sure?'               | The mesage to show                     |
| **confirmationMessage**  | String       | 'I really want to do it'      | The message the user will need to type  |
| **options**              | Object       | *see below*                   | The custom options                     |

###### options
| Option       | Type    | Default                                                                                                                | Description                                                                                         |
|--------------|---------|------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| **duration** | Integer | 5                                                                                                                      | How many seconds the user will need to press the confirmation button                                |
| **labels**   | Object  | {ok: *'Yes, i\'m sure'*, cancel: *'Cancel'*, pressing: *'Keep pressing...'*, confirmed: *'Confirmed, please wait...'*} | The labels of the \<ok\> and \<cancel\> buttons, and \<pressing\>, \<confirmed\> states for the \<ok\> button |

