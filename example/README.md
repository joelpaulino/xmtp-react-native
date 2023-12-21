# XMTP React Native example app

This basic messaging app has an intentionally unopinionated UI to help make it easier for you to build with.

## Run the example app
Follow the [React Native guide](https://reactnative.dev/docs/environment-setup) to set up a CLI environment.

To use the example app, run:

```bash
yarn
cd example
yarn
npx pod-install
yarn run [ios or android]
```

## Run example app unit tests on local emulators
Running tests locally is useful when updating GitHub actions, or locally testing between changes.

1. [Install Docker](https://docs.docker.com/get-docker/)

2. Start a local XMTP server (from example directory)
    ```bash
    docker-compose -p xmtp -f dev/local/docker-compose.yml up -d
    ```
3. Verify the XMTP server is running
    ```bash
    docker-compose ls

    NAME                STATUS              CONFIG FILES
    xmtp                running(3)          <REPO_DIRECTORY>/xmtp-react-native/example/dev/local/docker-compose.yml
    ```
4. You can now run unit tests on your local emulators
5. You can stop the XMTP server with the following command:
    ```bash
    docker-compose -p xmtp -f dev/local/docker-compose.yml down
    ```

## Run e2e tests for example app
Running e2e tests when updating example app with Detox

1. Setup [Detox Prerequisites](https://wix.github.io/Detox/docs/introduction/environment-setup#detox-prerequisites)

2. Update example/.detoxrc.js to match device configs - [More information on device config and debugging issues](https://wix.github.io/Detox/docs/introduction/project-setup#step-3-device-configs)

3. Build the app for testing: 
```bash
    detox build --configuration ios.sim.debug
```
or
```bash
    detox build --configuration android.emu.debug
```
4. Run the tests:
```bash
    detox test --configuration ios.sim.debug
```
or
```bash
    detox test --configuration android.emu.debug
```
