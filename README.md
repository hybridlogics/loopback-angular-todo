# Wiring Up Loopback With AngularJs - Part 2

## Todo App

Open terminal / cmd(command-line)

```
git clone https://github.com/hybridlogics/loopback-angular-todo.git
cd loopback-angular-todo
npm install
node . 
then browse to localhost:3000
```

A simple todo list using AngularJS on the client-side and LoopBack on the
server-side.

## Prerequisites

### Tutorials

- [Wiring Up Loopback With AngularJs - Part 1](https://github.com/hybridlogics/loopback-angular-setup).

### Knowledge of

- [Angular](https://angularjs.org/)
- [Angular Resource](https://docs.angularjs.org/api/ngResource/service/$resource)
- [AngularUI Router](https://github.com/angular-ui/ui-router)
- [Bootstrap](http://getbootstrap.com/)
- [Bower](http://bower.io/)
- [LoopBack](http://loopback.io/)
- [LoopBack AngularJS SDK](http://loopback.io/doc/en/lb2/AngularJS-JavaScript-SDK.html)
- [LoopBack models](http://loopback.io/doc/en/lb2/Defining-models.html)
- [LoopBack middleware](http://loopback.io/doc/en/lb2/Defining-middleware.html)

## Procedure

### Create the application

#### Application information

- Name: `loopback-angular-todo`
- Directory to contain the project: `loopback-angular-todo`

```
slc loopback loopback-angular-todo
... # follow the prompts
cd loopback-angular-todo
```

### Create the `Todo` model

#### Model information

- Name: `Todo`
  - Data source: `db (memory)`
  - Base class: `PersistedModel`
  - Expose over REST: `Yes`
  - Custom plural form: *Leave blank*
  - Properties:
    - `name`
      - String
      - Required
    - `description`
      - String
      - Required

```
slc loopback:model Todo
... # follow the prompts
```

### Configure the vendor directory


>Bower installs packages in `bower_components` 

### Install client-side dependencies

From the project root, run:

```
bower install angular angular-resource angular-ui-router bootstrap
```

### Create the home page

Create [`index.html`]in the client directory.

### Create the main stylesheet

Create a css directory to store stylesheets.

```
mkdir client/css
```

In this directory, create [`styles.css`]

### Serve static assets from the `client` directory

Delete `/server/boot/root.js`.

Add static middleware to the [`files` section in `middleware.json`]
.

### Create `app.js`

Create a [`js` directory](https://github.com/strongloop/loopback-example-angular/blob/master/client/js) to hold scripts files.

```
mkdir client/js
```

In this directory, create [`app.js`]

>Notice we declare [`lbServices`] as a dependency. We
will generate this file using the `lb-ng` command in a later step.

### Create `todo.html`

Create a [`views`] to store view templates.

```
mkdir client/views
```

In this directory, create [`todo.html`].

### Create `controllers.js`

Create a [`controllers`]  directory to store controller
files.

```
mkdir client/js/controllers
```

In this directory, create [`todo.js`]

### Generate `lb-services.js`

Create a [`services` directory] to store service files.

```
mkdir client/js/services
```

`lb-ng` is automatically installed along with the `slc` command-line tool (ie.
when you ran `npm install -g strongloop`). `lb-ng` takes two arguments: the
path to [`server.js`] and the path
to the [generated services file].
[`lb-services.js`] is an Angular service
used to interact with LoopBack models.

Create [`lb-services.js`]  using the `lb-ng`
command.

```
lb-ng server/server.js client/js/services/lb-services.js
```

### Run the application

From the project root, enter `node .` and browse to [`localhost:3000`](http://localhost:3000)
to view the application.

---

