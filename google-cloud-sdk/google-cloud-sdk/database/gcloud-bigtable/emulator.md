---
description: >-
  The Cloud SDK provides a local, in-memory emulator for Cloud Bigtable, which
  you can use to test your application.
---

# emulator

You can use the emulator with all Cloud Bigtable client libraries except for the PHP client library.

## Installing the emulator

To install the Cloud Bigtable emulator:

1. [Install the Cloud SDK](https://cloud.google.com/bigtable/docs/installing-cloud-sdk).
2. Update your `gcloud` command-line tool installation to get the latest features:

   ```text
   gcloud components update beta
   ```

3. Run the following command to start the emulator:

   ```text
   gcloud beta emulators bigtable start
   ```

   If the emulator is not installed already, you will be prompted to download and install the binary for the emulator.

4. Type Control-C to stop the emulator.

## Using the emulator

To use the Cloud Bigtable emulator:

1. Run the following command to start the Cloud Bigtable emulator:

   ```text
   gcloud beta emulators bigtable start
   ```

   The emulator prints the host and port number where it is running.

   By default, the emulator chooses `localhost:8086`. To bind the emulator to a specific host and port, use the optional `--host-port` flag, replacing \[HOST\] and \[PORT\]:

   ```text
   gcloud beta emulators bigtable start --host-port=[HOST]:[PORT]
   ```

2. In the environment for your application, set the `BIGTABLE_EMULATOR_HOST` environment variable to the host and port where the Cloud Bigtable emulator is running \(for example, `myhost.example.com:8010`\).

   If you are running the emulator on the same machine as your application, you can use the following command to set this environment variable automatically:

   ```text
   $(gcloud beta emulators bigtable env-init)
   ```

   Setting this environment variable causes the application to run in the emulator, with no further action required. The client automatically uses the variable if it is set, instead of connecting to the Cloud Bigtable service.

3. When you are done using the emulator, type Control-C to stop the emulator.

