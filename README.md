# GraphQL Restaurant Data Exercise from Module 24

Exercise from Module 24 using NodeJS, Express, and GraphQL

## Overview

This was created to submit for an assignment in Module 24 of the MIT xPRO Full Stack Development course (Fall 2022).
The exercise included the following details, which are implemented in the app:

Your task is to set up GraphQL for your restaurant data and then add mutations to get and update these data.

Implement the following methods under the “root” object:

- restaurant: This gets a single restaurant based on a provided ID
- restaurants: This gets a list of all restaurants
- setRestaurant: This creates a new restaurant
- deleteRestaurant: This deletes a restaurant based on the provided id.
- editRestaurant: This updates a restaurant based on the provided id.

### Instructions:

After completing the task, run the GraphQL interface and submit a file with screenshots showing all five queries and mutations highlighted above, along with a link to your GitHub repo that houses the code for this activity.

## Details & Improvements

I made a few changes to the code as a learning exercise, so that I may better understand GraphQL.

- Added `id` property to restaurant(s) queries.
- When `setRestaurant` is run, it will also add a sequential id to the newest restaurant.
- Changed `deleteRestaurant` to use `splice()` instead of `filter()`.
- `editRestaurant` correctly sets the description now.
- Added validation to the `getRestaurant` query. It will give an error if the id does not exist.

## How to Run

Download the source code, run `npm install`, then run `node index.js`. Navigate in your web browser to `http://localhost:5500/graphql`.

### GraphQL Queries

<details>
<summary>Below is the list of queries/mutations used in this exercise:</summary>

```
query getRestaurants {
  restaurants {
    id
    name
    description
    dishes {
      name
      price
    }
  }
}

query getRestaurant($iid: Int = 1) {
  restaurant(id: $iid) {
    id
    name
    description
  }
}

mutation setRestaurants {
  setRestaurant(input: {
    	name: "Granite",
    	description: "American"})
  {
    name
    description
  }
}

mutation editRestaurants($iid: Int = 3, $name: String = "Slate", $description: String = "American2") {
  editRestaurant(id: $iid, name: $name, description: $description) {
    name
    description
  }
}

mutation deleteRestaurants($iid: Int = 1) {
  deleteRestaurant(id: $iid) {
    ok
  }
}

variables = {
  "iid": 3
}

```

</details>
