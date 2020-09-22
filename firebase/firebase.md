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

