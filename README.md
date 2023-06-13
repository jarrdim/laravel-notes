# laravel-notes

#MVC -> Model view controller

Framework  is the skeleton of a project,intead of starting from scratch
PHP Basics
PHP Object oriented Programming

OOP CONCEPTS (OBJECT ORIENTED PROGRAMMING)
Classes and Objects:

    A class is a blueprint for creating objects. It defines the properties and methods that objects of
    that class will have.
    An object is an instance of a class, representing a specific entity with its own state and behavior.

Encapsulation:

    Encapsulation is the principle of bundling data (properties) and related behaviors (methods) 
    together in a class.
    It allows for data hiding and protects the internal state of an object, providing controlled 
    access through public, private, and protected visibility modifiers.

Inheritance:

    Inheritance is a mechanism that allows a class to inherit properties and methods from a parent class.
    It enables code reuse and supports the concept of hierarchical relationships between classes.
    The child class (subclass) extends the parent class (superclass) to inherit its characteristics 
    and can also add its own unique properties and methods.

Polymorphism:

    Polymorphism allows objects of different classes to be treated as objects of a common parent class.
    It enables the use of a single interface or method to handle objects of multiple types,
    providing flexibility and extensibility.
    Polymorphism is achieved through method overriding and interface implementation.

Abstraction:

    Abstraction focuses on defining the essential features and behaviors of an object 
    while hiding unnecessary details.
    Abstract classes cannot be instantiated, while interfaces define a contract that
    implementing classes must fulfill.

Autoloading and Namespaces:

    Autoloading eliminates the need to manually include class files by defining a mapping between 
    class names and file paths.
    Namespaces provide a way to organize classes into logical groups and prevent naming conflicts.

    WELCOME TO LARAVEL

1. Introduction to MVC:

        MVC is a software architectural pattern used in web development.
        It separates the application logic into three components: the Model, View, and Controller.
        The Model represents the data and business logic, the View is responsible for displaying 
        the user interface, and the Controller handles the user's requests and updates
        the Model and View accordingly.

2. Benefits of MVC:

        Separation of concerns: MVC promotes a clear separation between the different aspects of 
        an application, making it easier to maintain and modify.
        Code reusability: With a well-structured MVC architecture, components can be reused across
        different parts of the application.
        Testability: The separation of concerns facilitates unit testing and enables developers to 
        test individual components in isolation.

3. Understanding Laravel:

        Laravel is a popular PHP web framework that follows the MVC pattern.
        It provides a robust set of tools and features for building scalable and 
        maintainable applications. Laravel emphasizes convention over configuration, which 
        means it includes predefined conventions and structures that simplify development.

4.  Key Components of Laravel:

    a. Routes:
        Routes define the URLs and corresponding actions (controllers) in your application.
        Laravel uses a dedicated file, routes/web.php or routes/api.php, to define these routes.
        Routes map URLs to specific actions in controllers.

        EXAMPLES.
        // Define a basic GET route
        Route::get('/home', 'HomeController@index');

        // Define a route with a parameter
        Route::get('/users/{id}', 'UserController@show');

        // Define a route with multiple HTTP verbs
        Route::match(['get', 'post'], '/users', 'UserController@store');

        // Define a route with a wildcard parameter
        Route::get('/users/{id}/profile', function ($id) {
            return "User Profile: " . $id;
        });


    b. Controllers:
    
        Controllers handle the logic behind the user's requests.
        They receive the request, interact with the models, and return a response.
        Controllers are stored in the app/Http/Controllers directory.

    c. Models:
        Models represent the data and business logic of the application.
        They encapsulate database interactions and define relationships between entities.
        Models are typically located in the app/Models directory.

        . Creating a Model in Laravel:

            .Models represent database tables and encapsulate data logic.
            .Laravel provides an easy way to create models using the make:model Artisan command.

                php artisan make:model User

            .This will generate a User model file in the app/Models directory.


    d. Views:
    
        Views are responsible for presenting the user interface to the user.
        Laravel uses the Blade templating engine, which allows you to create reusable templates
        with dynamic content. Views are stored in the resources/views directory.

    e. Migrations:
    
        Migrations are used to manage the database schema.
        Laravel provides a simple and expressive way to create, modify, and roll back database tables
        and columns using migration files.

    f. Eloquent ORM:
    
       Laravel's Eloquent ORM (Object-Relational Mapping) provides a convenient way to interact
       with the database using PHP syntax.
       It allows you to define relationships between models and perform 
       database operations with ease.

       Retrieving Data with Eloquent ORM:

       Laravel's Eloquent ORM provides a fluent query builder and an easy-to-use syntax for database operations.

        EXAMPLE:

        // Retrieve all users
        $users = User::all();

        // Retrieve a user by primary key
        $user = User::find(1);

        // Retrieve users based on a condition
        $users = User::where('age', '>', 25)->get();

        // Retrieve the first user that matches a condition
        $user = User::where('name', 'John')->first();

        // Limit the number of retrieved users
        $users = User::take(10)->get();


## Training Tips:

        Provide hands-on examples and exercises to reinforce the learning.
        Encourage exploration of the Laravel documentation for a deeper understanding.
        

6. Blade Templating in Laravel:

        Laravel uses the Blade templating engine for creating dynamic views.
        EXAMPLE

            <!-- Display a variable value in a Blade template -->
        <h1>Welcome, {{ $user->name }}</h1>

        <!-- Execute PHP logic in a Blade template -->
        @if($user->isAdmin)
            <p>User is an admin.</p>
        @else
            <p>User is not an admin.</p>
        @endif

        <!-- Include a Blade partial template -->
        @include('partials.header')

        <!-- Loop through an array in a Blade template -->
        @foreach($users as $user)
            <p>{{ $user->name }}</p>
        @endforeach

7. Form Handling and Validation:

        Laravel provides convenient methods for handling form input and performing validation.

        EXAMPLE:

        // Validate form input
        $validatedData = $request->validate([
            'name' => 'required',
            'email' => 'required|email|unique:users',
            'password' => 'required|min:8',
        ]);

        // Display validation errors in a Blade template
        @error('name')
            <div class="alert alert-danger">{{ $message }}</div>
        @enderror
        
 Create a Migration:

   Use the make:migration Artisan command to generate a new migration file.
    
        php artisan make:migration create_users_table
   Run migration
   
        php artisan migrate
 Create a Model:
    Use the make:model Artisan command to generate a new model file.
    
        php artisan make:model User
        
Generate Resourceful Controller:
    Use the --resource or --api option to generate a resourceful controller for the model.

    php artisan make:controller ProductController --resource
    
    //or without resource
    
    php artisan make:controller ProductController

   This will generate a ProductController with resourceful methods like index, create, store, show, edit, update, destroy, etc.




