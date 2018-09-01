# Angular 2

4 Key Players in Angular 2 app

* Components
* Directives
* Routers
* Services

# Components

Encapsulates the template, data, and the behaviors of the view. - (a view component)

Each app has a root component, and likely many many more

    Components can have components in them

export class RatingComponent {

  averageRating: number;

  setRating(value){
    ...
  }
}

* They encapsulate the template, data and logic of a view
* They're plain typescript classes
* They can be re-used

# Services

We use services to encapsulate any non-UI logic
Any logic not related to view
(data access, logging, business logic, etc)


# Routers

Used to control navigation.
They are often used in Single Page Applications (SPA)s

# Directives

Used to modify DOM elements and/or extend their behavior

# Modules

A block of highly related classes.
