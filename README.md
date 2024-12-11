# EduKUDO Task


> **Introduction**  
This task, created by **Tej Dahal**, is a Laravel-based project utilizing Inertia.js, Vue.js 3, Vite.js, Docker, and Sail. Follow the guide below to set up the application.

> **Note:** Docker and Docker Compose are required to run this application.

# Tasks Overview

## Task 1: Parent and Child Components
- Created a parent component with two variables:
    - A boolean
    - A string
- Child component:
    - Toggles the boolean value.
    - Updates the string via a text box.
- Used props and events for communication between parent and child components.

## Task 2: LESS Compiler and Live Preview
- Built a real-time editor with:
    - Input for HTML and LESS.
    - Live LESS compilation (debounced).
    - Isolated preview area with scoped styles.
- Preview dynamically updates based on inputs.

## Files

### Main Component
- `resources/js/Pages/Welcome.vue`

### Parent and Child Components
- `resources/js/EduKudoComponents/ParentComponent.vue`
- `resources/js/EduKudoComponents/ChildComponent.vue`

### LESS Editor
- `resources/js/EduKudoComponents/LessEditorComponent.vue`

---

## Installation Guide

### Prerequisites
Ensure you have Docker and Docker Compose installed on your system before proceeding.



### Getting Started

#### Clone the Repository

```bash
git clone git@github.com:dahaltn/eduKudo.git
cd ./eduKudo

```
Next, we can install eduKudo test project with these **4 simple steps**:

### 1. Install php composer dependencies.

Run this command from the project folder after cloning the repo.

```bash
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php84-composer:latest \
    composer install --ignore-platform-reqs
```
Alias sail command
```Bash
alias sail='[ -f sail ] && sh sail || sh vendor/bin/sail'
```

### 2. Duplicate the `.env.example` file and name it to `.env`

```Bash
cp .env.example .env
```

Then, open up the `.env` file and update your `DB_DATABASE`, `DB_USERNAME` and `DB_PASSWORD` in the appropriate fields. Also update the `APP_URL` to the URL of your application.

``` Database setup is optional for this test task. ```

```env
APP_URL=http://localhost

DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=sail
DB_PASSWORD=password
```

Note: If you forget to create the .env file prior to executing `sail up -d`, the database credentials will default to the values specified in the example above

### 3. Build and run containers

Run sail build --no-cache to build fresh containers.

*Note: No need to run this command if you have already build images.*

```bash
sail build --no-cache
```
Run containers
```bash
sail up -d
```

### 4. Install Dependencies

We need to install npm dependencies,  to install all packages, please run commands below.
```bash
## Install php dependencies.
sail composer install
```

```bash
## Install js dependencies.
sail npm install
```

```bash
## Compile JS files.
sail npm run build
sail npm run dev (To watch live changes)
```
### 4. Install Migration (optional)

You must migrate database schema into database, which we can accomplish by running the following command:
```php
sail artisan migrate
```
<br>

🎉 And that's it! You will now be able to visit your URL and see the application up and running.


### Watch, Learn, and Build

Everytime we make changes to JS files it must be compiled to be able to reflect the JS changes, please use below command.

```bash
sail npm run dev
```
**Note:** if any reason ``sail`` command not working, you can use run ``./vendor/bin/sail <command to run>`` from project folder 
