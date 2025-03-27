# Code Editor Integration Development
![Node.js CI](https://img.shields.io/github/workflow/status/gleitz/howdoi/Node.js%20CI?color=78dce8&label=Node.js%20CI&style=plastic)

Simplifies the process of integrating howdoi as a code editor extension.

## Description

The Code Editor Integration plug-in is ran by calling the `runHowdoi` function which takes in a user's query of type string. The parameter is encapsulated by a single line comment and is formatted as follows:

    // howdoi query

`runHowdoi` returns an Object with the structure:

    {
        question: string
        answer: string[]
        link: string[] 
    }

The Object values:
* question contains the user's query encapsulated by a single line comment
* answer contains the three possible answers to the user's query 
* link contains the three possible links to the answer encapsulated by a single line comment


## Installation

First, install howdoi on your machine.

Then, install all necessary packages:

    npm install

## Development

To compile the script:

    npm run compile

To run the script:

    npm start

To compile and run the script:

    npm run build

To run the testing script:

    npm test

## Integration

To utilize this plug-in to create a howdoi extension for a code editor: 

1. Copy the `code-editor-integration` folder into your workspace and remove the `node_modules` folder by adding the script
    
        "copy": "ncp ../code-editor-integration/ src/code-editor-integration/"
        "clean": "rimraf ./src/code-editor-integration/node_modules"
  
    into your `package.json` file and running it.
    First, you will need to install [ncp](https://www.npmjs.com/package/ncp) and [rimraf](https://www.npmjs.com/package/rimraf).

2. Import the `plugin.ts` file into your main file.
    
3. Call the `runHowdoi` function.

Refer to `vscode-howdoi` for an example.

## Usage

usage: 
    
    // howdoi query [-n NUM_ANSWERS]

positional arguments:

      QUERY                 the question to answer

optional arguments:

      -n NUM_ANSWERS        NUM_ANSWERS
                            number of answers to return
                            (default: 3)

## Integrating howdoi with an AI/ML Ops pipeline

To integrate howdoi with an AI/ML Ops pipeline, follow these steps:

1. Install howdoi on your machine by following the [installation instructions](https://github.com/gleitz/howdoi#installation).

2. Use the `howdoi` command in your pipeline scripts to fetch answers to coding questions. For example, you can use howdoi to get the syntax for a specific programming task:

    ```bash
    howdoi create tar archive
    ```

3. Integrate howdoi as an extension in your code editor to streamline the development process. Follow the instructions in the "Integration" section above to create a howdoi extension for your code editor.

## Examples

Here are some examples of using howdoi in pipeline scripts to fetch answers and automate coding tasks:

1. Fetching the syntax for creating a tar archive:

    ```bash
    #!/bin/bash
    TAR_SYNTAX=$(howdoi create tar archive)
    echo "Creating tar archive using the following syntax:"
    echo "$TAR_SYNTAX"
    ```

2. Fetching the syntax for formatting a date in bash:

    ```bash
    #!/bin/bash
    DATE_SYNTAX=$(howdoi format date bash)
    echo "Formatting date using the following syntax:"
    echo "$DATE_SYNTAX"
    ```

3. Fetching the syntax for printing a stack trace in Python:

    ```python
    import os

    stack_trace_syntax = os.popen('howdoi print stack trace python').read()
    print("Printing stack trace using the following syntax:")
    print(stack_trace_syntax)
    ```
