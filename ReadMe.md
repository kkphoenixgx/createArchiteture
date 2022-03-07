# CreateDir Setup

Hello, my nickname is kkphoenix, I am a web develop from Brazil, I am just 16 now but I created this architecture project to facilitate my work creating project directories, I think that can help a lot of people and as you probably noticed, the project is a js/nodejs project and is pretty scalable, you can create your own architecture and have a great time with this start project.
You can use the project by entering in the repository cloned and using:

> npm start

## How I create my own architecture?

To create our own architecture, just follow some rules:

* You have to start by scribing the name of your architecture on the [indexSetup.js](./indexSetup.js): line 43:

  ~~~js
  choices: ['React', 'Node', 'Express', 'MVC', 'THE NAME OF YOUR ARCHITECTURE'],
  ~~~

* After that, you have to create your own architecture file, create file in [Architectures](./Setup/Architectures/) and start creating the files and folders that are going to be in your architecture:  
  
  Copy and paste this base structure in your file:

  ~~~js
  import fs from 'fs'
  import chalk from 'chalk'

  // ----FOLDERS----
  const rootFiles = []; 
  // that will be the const that contains the folders of the root dir
  
  // ----FILES----
  const rootFiles = ['.gitignore', 'README.md'];
  // that will be the const that contains the files of the root dir
  
  
  // ----- BASE PROCESS -------

  export async function init(folderName, path){
    let createMvcArchitecture = new Promise( (resolve, reject) => {
        let COMPLETE_PATH = `${path}/${folderName}`;
        
        try{ createFoldersAndFiles(COMPLETE_PATH); resolve(true) }
        catch(err){ reject(err) }
    }) 
    return createMvcArchitecture
  }

  function createFoldersAndFiles(path){
    createBaseFolder(path);
    createRootFolders(path)

    createRootFiles(path);
  }

  //------- CREATING FOLDERS -------

  function createBaseFolder(path){
    fs.mkdir(path, { recursive: true }, function(error){
        if(error) throw error
        console.log( chalk.black('created root folder'))
    })
    }

    function createRootFolders(path){
        rootFolders.forEach(element => {
            fs.mkdir(`${path}/${element}`, function(error){
                if(error) throw error
                console.log( chalk.red(`created ${element} folder`))
            });
        });
    }

  // ------ CREATING FILES -------

  function createRootFiles(path){

    rootFiles.forEach(element => {
        
        let content

        switch(element){

            case '.gitignore':
                content = 'node_modules'
            break;
            default:
                content = ''

        }

        fs.writeFile(`${path}/${element}`, `${content}`, function(error) {
            if(error) throw error

            console.log(chalk.white(`created ${element} file`));

        })
    });
    }
  ~~~

  And now with this baser structure, just create the folders that you want to in other consts, and follow the path to create more files and folders, remember that you are going to separate de functions, if there is a folder named Src, in the root directory, you create another const and another function to it:

  To create directories:

  ~~~js
    function create_THE-DAD's-FOLDER-NAME_folders(path){
    THE_CONST_NAME_CREATED.forEach(element => {
        // Remember that we are looking the perspect of the base folder, that have those folders
        /* 
          So if the dad's folder have a dad, like the element grandpa, you have to write all
          the older parents ${path}/THE-GRANDPA-FOLDER-NAME/THE-DAD'S-FOLDER-NAME/${element}'
        */
        fs.mkdir(`${path}/THE-DAD'S-FOLDER-NAME/${element}`,{ recursive: true }, function(error){
            if(error) throw error
            console.log( chalk.green(`created ${element} in _THE-DAD's-FOLDER-NAME_ folder`))
        })
    })
  }
  ~~~

  To create files:

  ~~~js
  function create_THE-DAD's-FOLDER-NAME_Files(path){
    srcFiles.forEach(element => {

        let content;
        switch(element){
            default: 
                // here you can define the content of the file or the files adding a case, like in the rootFiles function ^^
                content= '';
            break;
        }

        // Remember that we are looking the perspect of the base folder, that have those folders
        /* 
          So if the dad's folder have a dad, like the element grandpa, you have to write all
          the older parents ${path}/THE-GRANDPA-FOLDER-NAME/THE-DAD'S-FOLDER-NAME/${element}'
        */
        fs.writeFile(`${path}/_THE-DAD's-FOLDER-NAME_/${element}`, `${content}`, (error)=>{
            if(error) throw error
            console.log(chalk.green(`created ${element} file`));
        });
    });
  }
  ~~~

* After creating the architecture, go to [startArchitectureSetup.js](./Setup/startArchitectureSetup.js) and you have to import in the top of the file the architecture that you created

~~~js
import {init as initTHE_NAME_OF_YOUR_ARCHITECTURE } from './Architectures/THE NAME OF YOUR FILE.EXTENSION'
~~~

Create after the case MVC you own case of the switch after the break in line: 67

  ~~~js
        break;
    case 'THE NAME OF YOUR ARCHITECTURE'

        await sleep
        await initTHE_NAME_OF_YOUR_ARCHITECTURE(FOLDER_NAME, PATH).then( message => {
            
            if( message == true ) spinner.success({text : 'Content created'});
            
            if( message == false ) spinner.error({ text : chalkAnimation.glitch('THAT IS A ERROR').start() })

            
            let COMPLETE_PATH = `${PATH}/${FOLDER_NAME}`
            nodeInit(ARCHITECTURE, COMPLETE_PATH)
        })
  ~~~

* After all of it is pretty simple, just go to the [npmStart](Setup/npmStart.js) and follow that path after the break of line 120:

~~~js
case 'THE NAME OF YOUR ARCHITECTURE'
    await sleep();

    // put the name of the framework that you want to start, here
    let NPM_FRAMEWORK_THAT_YOU_CHOICE = 'THE NAME OF OF THE FRAMEWORK'

    // Attention because the name of the constant is hardcoded
    const spinnerNPM_FRAMEWORK_THAT_YOU_CHOICE = createSpinner('installing ${NPM_FRAMEWORK_THAT_YOU_CHOICE...}').start();
    await sleep();

    exec(`npm install ${NPM_FRAMEWORK_THAT_YOU_CHOICE} --prefix ${path}`, (error, stdout, stderr) =>{ 
        if(error){
            SPINNER_NPM_FRAMEWORK_THAT_YOU_CHOICE.error();
            return console.error(`error: ${error.message}`)
        }

        if(stderr){
            SPINNER_NPM_FRAMEWORK_THAT_YOU_CHOICE.error();
            return console.error(`stderr: ${stderr}`)
        }

        SPINNER_NPM_FRAMEWORK_THAT_YOU_CHOICE.success();
        console.log(`stdout: \n ${stdout}`);
    });
~~~

* now shut up and wun it.
