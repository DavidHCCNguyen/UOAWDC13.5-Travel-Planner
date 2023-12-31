# 13 Mini-Project: Travel Planner

## Instructed Notes

* As a traveller, I want to be able to create an account.

* As a traveller, I want to be able to create a new trip for myself using a location from a list.

* As a traveller, I want to be able to create and view location data.

* As a traveller, I want to be able to view all of the trips I'm taking, along with their locations.

## Criteria

* It's done when the GET route `/api/travellers` returns all traveller data without associated trips in Insomnia.

* It's done when the POST route `/api/travellers` creates traveller data and returns a successful response in Insomnia.

* It's done when the GET route `/api/travellers/:id` returns a single traveller's data with their associated trips and a list of locations in Insomnia. 

* It's done when the DELETE route `/api/travellers/:id` removes a traveller and any trips associated with them and returns a successful response in Insomnia.

* It's done when the GET route `/api/locations` returns all location data in Insomnia.

* It's done when the POST route `/api/locations` creates location data and returns a successful response in Insomnia.

* It's done when the GET route `/api/locations/:id` returns a single location's data, with its associated trips, in Insomnia. 

* It's done when the DELETE route `/api/locations/:id` removes a location and any trips associated with it and returns a successful response in Insomnia.

* It's done when the POST route `/api/trips` creates trip data between associated travellers and locations.

* It's done when the DELETE route `/api/trips/:id` removes a trip and returns a successful response in Insomnia.

* It's done when the API is successfully deployed to Heroku with a MySQL database.

## Specifications 

* Database models should have the following fields and associations:

  * `Traveller`

    * `id`: primary key

    * `name`
      
    * `email`

  * `Location`

    * `id`: primary key
    
    * `location_name`

  * `Trips`
      
    * `id`: primary key

    * `trip_budget` 
      
    * `traveller_amount`
      
    * `traveller_id`: non-unique foreign key that references the `Traveller` model's `id` field (`Traveller.id`)

    * `location_id`: non-unique foreign key that references the `Location` model's `id` field (`Location.id`)

  * Travellers have many locations, and locations have many travellers through trips (many-to-many association).

  * Set the `unique` flag to `false` to avoid a SQL error when creating the many-to-many relationship, because travellers can take multiple trips.

## 📝 Notes

Refer to the documentation: 

* [Sequelize documentation on many-to-many relationships](https://sequelize.org/master/manual/assocs.html#many-to-many-relationships)

* [The Full-Stack Blog guide to deploying with Heroku and MySQL](https://coding-boot-camp.github.io/full-stack/heroku/deploy-with-heroku-and-mysql)

Use the following sample data as the request body POST `/api/trips` route:

  ```json
  {
    "trip_budget": 2000.50,
    "traveller_amount": 6,
    "traveller_id": 1,
    "location_id": 2
  }
  ```

---

## 💡 Hints

* What model association option can we set to automatically delete associated data? 

* How can we use the data in `Develop/seeds` to provide starter data for locations and travellers and not have to create it ourselves? 

* If we're deploying this to Heroku, can we work on this from within the class repository, or should we make a new GitHub repo?