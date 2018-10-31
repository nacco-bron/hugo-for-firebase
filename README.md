# hugo-for-firebase 

## Using on CircleCI 2.0

Using following configuration in `.circleci/config.yml `

```
version: 2
jobs:
  build:
    docker:
      - image: naccobron/hugo-for-firebase:latest
    working_directory: ~/project
    steps:
      - checkout
      - run:
          name: "Run Hugo"
          command: hugo
      - deploy:
          branch: master
          command: firebase deploy --token "$FIREBASE_TOKEN"
```
The environment variable `FIREBASE_TOKEN` stores the Firebase authentication token and is saved in `Build Setting > Environment Variables` on CircleCI console.