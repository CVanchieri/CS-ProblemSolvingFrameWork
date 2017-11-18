**WIP**

## Prerequisites

First, go to the extensions panel in VS Code and search for `C/C++`. Choose the extension by Microsoft (ms-vscode.cpptools).

Install that extension and restart VSC.


## Building the Project in VSC

What we want to be able to do is build the project with CTRL-SHIFT-B (or COMMAND-SHIFT-B).

The `tasks.json` file controls which tasks VSC can run. The one we're interested in is the Default Build Task.

1. With VSC open to your root project directory, hit CTRL-SHIFT-P (or COMMAND-SHIFT-P).
2. Type `tasks` and choose "Tasks: Configure Default Build Task".
3. Choose "Create tasks.json file from template".
4. Choose "Others".

At this point you should be editing `tasks.json`.

1. Change the `label` to something representative, like `Build`
2. Change the `command` to the command you want to run, like `gcc -Wall -o foo foo.c` or `make`
3. Hit CTRL-SHIFT-P (or COMMAND-SHIFT-P) again.
4. Type `tasks` and choose "Tasks: Configure Default Build Task" again.
5. Select the value you put in for `label` in step 1.
6. Save `tasks.json`.

At this point, your `tasks.json` should look something like this:

```javascript
{
  // See https://go.microsoft.com/fwlink/?LinkId=733558
  // for the documentation about the tasks.json format
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Build",
      "type": "shell",
      "command": "make",
      "group": {
        "kind": "build",
        "isDefault": true
      }
    }
  ]
}
```

Now you should be able to hit CTRL-SHIFT-B (or COMMAND-SHIFT-B) and see a build.

### Adding PROBLEMS Panel Support

Adding a _Problem Matcher_ will automatically extract error information from the build and put it in the PROBLEMS panel to make it easier to jump to those line numbers.

Here is a `tasks.json` file with a [`problemMatcher` for C/C++](https://code.visualstudio.com/docs/editor/tasks#_defining-a-problem-matcher) added in:

```javascript
{
  // See https://go.microsoft.com/fwlink/?LinkId=733558
  // for the documentation about the tasks.json format
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Build",
      "type": "shell",
      "command": "make",
      "group": {
        "kind": "build",
        "isDefault": true
      },
      "problemMatcher": {
        "owner": "cpp",
        "fileLocation": ["relative", "${workspaceFolder}"],
        "pattern": {
          "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning|error):\\s+(.*)$",
          "file": 1,
          "line": 2,
          "column": 3,
          "severity": 4,
          "message": 5
        }
      }
    }
  ]
}
```

## Debugging the Project in VSC

WIP