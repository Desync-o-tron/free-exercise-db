## Free Exercise DB 💪  &nbsp; [![Lint & Deploy Site to Github Pages](https://github.com/yuhonas/free-exercise-db/actions/workflows/build-site.yaml/badge.svg)](https://github.com/yuhonas/free-exercise-db/actions/workflows/build-site.yaml)


Open Public Domain Exercise Dataset in `JSON` format, over 800 exercises & images with a browsable public searchable frontend

### Why?

I started building another fitness related app and was looking for free/open source exercise lists and imagery I stumbled upon
[exercises.json](https://github.com/wrkout/exercises.json) which was amazing though the data wasn't structured the way I wanted it and I also wanted a free browsable/searchable frontend to the data inspired by [this issue](https://github.com/wrkout/exercises.json/issues/5) so I restructured the data and built a simple frontend to it :)

### What do they look like?

All exercises are stored as seperate `JSON` documents and conform to the following [JSON Schema](./schema.json) eg.

```json
{
  "name": "Alternate Incline Dumbbell Curl",
  "force": "pull",
  "level": "beginner",
  "mechanic": "isolation",
  "equipment": "dumbbell",
  "primaryMuscles": [
    "biceps"
],
"secondaryMuscles": [
  "forearms"
],
"instructions": [
  "Sit down on an incline bench with a dumbbell in each hand being held at arms length. Tip: Keep the elbows close to the torso.This will be your   starting position."
],
"category": "strength",
"images": [
  "Alternate_Incline_Dumbbell_Curl/0.jpg",
  "Alternate_Incline_Dumbbell_Curl/1.jpg"
]}
```
See [Alternate_Incline_Dumbbell_Curl.json](./exercises/Alternate_Incline_Dumbbell_Curl.json) 
 
### How do I use them?

You can use the `JSON` files independantly or combine them into a single `JSON` file containing an array of objects using the following make task

```sh
make dist/exercises.json
```
_Note: requires [jq](https://stedolan.github.io/jq/)_

### Importing into PostgreSQL

To combine all `JSON` files into Newline Delimeted `JSON` suitable for import into PostgreSQL use the following make task

```sh
make dist/exercises.nd.json
```
_Note: requires [jq](https://stedolan.github.io/jq/)_

See also [Makefile](./Makefile)

### Browsable frontend

<img src="./site/public/screenshot.png" alt="Screenshot of browsable frontend" width="500">

There is a simple searchable/browsable frontend to the data written in [Vue.js](https://vuejs.org/)  available at [https://yuhonas.github.io/free-exercise-db/](https://yuhonas.github.io/free-exercise-db/), all related code is in the [./site](./site) directory


#### Setup

```sh
npm install
```

#### Compile and Hot-Reload for Development

```sh
npm run dev
```

#### Compile and Minify for Production

```sh
npm run build
```

#### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

#### Run End-to-End Tests with [Cypress](https://www.cypress.io/)

```sh
npm run test:e2e:dev
```

This runs the end-to-end tests against the Vite development server.
It is much faster than the production build.

But it's still recommended to test the production build with `test:e2e` before deploying (e.g. in CI environments):

```sh
npm run build
npm run test:e2e
```

#### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

### TODO

The following fields are incomplete in _some_ JSON files and in such have had to allow `null` in the JSON Schema

* force
* mechanic
* equipment

### Contribute
Contributions are always welcome! Please read the contribution guidelines first.

### Special Thanks 🙇
To [Ollie Jennings](https://github.com/OllieJennings) for the original dataset at [exercises.json](https://github.com/wrkout/exercises.json)
