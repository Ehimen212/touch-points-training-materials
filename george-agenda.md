# Training Topic

## GCP Shell Commands

1.  What is a shell?

    - Shell types.
    - Recommended shells to use.

2.  GCP SDK<sup>1</sup>

    - What is Cloud SDK?
    - Installation<sup>2</sup>:
      - Windows<sup>3</sup>
      - Linux and Mac<sup>2</sup>
    - Getting Help in the SDK Shell
    - Basic<sup>5</sup> Command Structure for Cloud Shell.

      > Within each release level, gcloud CLI commands are organized into a nested hierarchy of command groups, each of which represents a product or feature of the Cloud Platform or its functional subgroups.


      | Command  group 	| Description |
      -------------------|-------------|
      | gcloud compute   | Commands related to Compute Engine in general availability |
      | gcloud compute   | instances Commands related to Compute Engine instances in general availability |
      | gcloud beta compute | Commands related to Compute Engine in Beta |
      | gcloud alpha app | Commands related to managing App Engine deployments in Alpha |


         > Global flags

         - The gcloud CLI provides a set of gcloud CLI-wide flags that govern the behavior of commands on a per-invocation level. Flags override any values set in SDK properties.

        > Positional Arguments and Flags

         - While both positional arguments and flags affect the output of a gcloud CLI command, there is a subtle difference in their use cases. A positional argument is used to define an entity on which a command operates while a flag is required to set a variation in a command's behaviour.

1: [GCP SDK](https://cloud.google.com/sdk)

2: [SDK Installation Quick Starts](https://cloud.google.com/sdk/docs/quickstarts)

3: [Windows Installation](https://cloud.google.com/sdk/docs/quickstart-windows)

4: [SDK Basics](https://cloud.google.com/sdk/gcloud)
