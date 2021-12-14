# Contact_List_using_vueJS

Running my Code 

If you want to run my attached code, you need to follow these steps: 
1. Run npm install in the extracted project folder to install all required dependencies => This will create a node_modules folder which is missing otherwise (it's not in the attachment because that would bloat the ZIP file) 
2. Run npm run serve to bring up the development server, view the app at localhost:8080 (or whichever port is shown in your terminal).



Side note: 
In case of error, when starting the server, use the solution below:

Syntax Error: Error: No ESLint configuration found in folder...

Solution: run the following command in the terminal:
npm remove @vue/cli-plugin-eslint

(because vue-cli 3 is using a zero configuration approach, the way to disable it is to just uninstall the module)

Vue CLI installed and used. The CLI ( @vue/cli ) is a globally installed npm package and provides the vue command in your terminal.

