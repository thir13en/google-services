# Firebase


Managed Databases by Google, you can find them [here](https://firebase.google.com/).


### Crating a test backend
1. Go to console
![fb1](./img/fb1.png)
1. Create a Project
1. Set up the name of the project
1. Go to Database
1. Add a Realtime Firebase Test Database

### Deploying an Ng App to a Firebase cloud
1. Install the firebase tools globally: `npm i -g firebase-tools`
1. Login in the firebase client with `$ firebase login`
1. In the root of your project run `$ firebase init hosting`
1. Select which of the projects you have on your firebase account is the one you want to link to the current repository.
1. Select the directory that contains the files you want to host on your `firebase hosting`
1. Set up url redirects to `index.html` in the dialog.
1. Do not override the `index.html` in the next dialog.
This ends up creating a `.firebaserc` and a `firebase.json` files in your repository.  
Now, for actually **deploying the application**, run `$ firebase deploy`. The console should display a success message with the url where our application has been deployed.  
Another way to open is by running the following command:
```bash
firebase open hosting:site 
```

### Firebase Cloud Functions
A `Firebase Cloud Function` is a small server side function running on `firebase` servers, that can perform some auxiliary task on our SPA, such as image or payment processing.  
To create a `Firebase Cloud Function` do the following:
1. run `$ firebase init`, a console dialog with a couple of questions will start. Answer `yes`when it prompts if you want to install `npm` dependencies now.
1. This creates a new folder named `functions`, with a `package.json` and just a few dependencies. The `entrypoint` for our `firebase` cloud functions is in the `index.ts` file of this folder. You have a `hello world` example of such a function in this very same file.
1. So now you need to redirect everything that does not match a get request for any of the files in your `SPA` to a `Firebase Cloud Function`, by editing the `firebase.json` file:
```json
{
	"hosting": {
		"public": "dist",
		"ignore": [
			"firebase.json",
			"**/.*",
			"**/node_modules/**",
		],
		"rewrittes": [
			{
				"source": "**",
				"destination": "./index.html" -> "functions": "<myCloudFunction>"
			}
		]
	},
	"functions": {
		"predeploy": "npm prefix \"RESOURCE_DIR\" run build"
	}
}
```
Now, in case of having an `index.html` file, you can delete it to redirect to the `Firebase Cloud Function`.

