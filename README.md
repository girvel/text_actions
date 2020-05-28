This is a simple Python package I used to test packaging mechanism in Python. Also it provides a possibility to manage your UI text commands in bash-like syntax like `:open last.org` or `delete 1`.

```python
from text_actions import ui_action

actions = []

@ui_action(actions, 'd', 'delete')
def delete_action(state, index='-1'):
    index = int(index)
    if index < 0:
        index += len(state.activities)
    state.activities = state.activities[:index] + state.activities[index + 1:]
```

This code will create a library of commands inside the actions variable, that you can use as argument in `apply_action`. First argument is always the state of application, other arguments are receivied from user's command. You probably should not worry about cast exceptions, I usually catch them in the UI code.