# Getting Started

## Access

### **Snowflake**

Community curators are granted access to a dev environment for testing and development of a data model. A member of Flipside's analytics team will need to grant you access, so please ask in the [# 🌲 | community-curation](https://discord.com/channels/784442203187314689/1053086214615466095) channel on Discord something along the lines of:

> Hi, I’m interested in doing data curation for Flipside, could you give me snowflake access please? I’d like my username to be:  `community_<insert_username>`

{% hint style="warning" %}
Access to Snowflake is granted for the sole purpose of community curation and testing your models. This password is not to be shared with anyone. If you know someone who would like to contribute as well, we will credential them separately. If you would like to work with Flipside data in a Snowflake environment, please see the section on [Data Shares](broken-reference) and reach out separately.
{% endhint %}

### **dbt cloud \[Optional]**

If you are unfamiliar with dbt, we suggest creating a free account to [dbt Cloud](https://cloud.getdbt.com/). dbt Labs has built an IDE for developing dbt models. Once the environment is set up with the proper credentials, connect to a fork of the [model repository](https://github.com/orgs/FlipsideCrypto/repositories) to begin editing or building your own. The cloud environment includes the option to preview the compiled SQL models so you can see output as you work. Additionally, the command line for running dbt includes built-in autocomplete for common dbt commands.

{% hint style="info" %}
Note: if you are using dbt Cloud, you will need to fork the main repository and link your dbt Cloud environment to the fork.
{% endhint %}

## **Software Setup**

### git

If you don't already have it installed, install git to your machine. [Here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) are [two guides](https://github.com/git-guides/install-git) that may assist you.

You will also need a [Github](https://github.com/) account to collaborate on the model repositories. Github also has an official command line tool, [`gh`](https://github.com/cli/cli#installation), that is useful for interacting with Github repositories.

Once set up, clone a copy of the repository of choice to your machine and checkout a branch to begin making your changes. Branch name should follow the convention:`community/<branch_name>`.

* Ex:  `git checkout -b community/my-new-model`

### Docker Environment

We have included a Dockerfile in eligible repositories to handle the installation of dbt on your behalf.&#x20;

1. Clone a repository, like [`ethereum-models`](https://github.com/FlipsideCrypto/ethereum-models)&#x20;
2. [Install Docker](https://docs.docker.com/get-docker/) to your machine.
3. Copy the details of [`.env.sample`](https://github.com/FlipsideCrypto/ethereum-models/blob/main/.env.sample) to a `.env` file with your credentials. The environment details, like account and database, will be pre-filled for you. All you should need to replace is the below with your previously provided username and password.
   * ```
     SF_USERNAME=<YOUR SNOWFLAKE USERNAME>
     SF_PASSWORD=<YOUR SNOWFLAKE PASSWORD>
     ```
4. Open a terminal window in the repository directory and run the command `make dbt-console`. If successful, a Docker container should spin up, install dbt, and open a console for you to run dbt commands. The container will read your `.env` file and should be connected to operate on the community curation database.
5. Test your connection!
   1. Run `dbt debug` to check installation.
   2. Run `dbt deps` to install dependencies listed in the [`packages.yml`](https://github.com/FlipsideCrypto/ethereum-models/blob/main/packages.yml).
   3. Run `dbt test -s core__fact_blocks` to run a set of tests on the `<chain>.core.fact_blocks` model in the community curation database to check your connection and credentials.
   4. If you run into any errors, reach out for assistance in the [Discord channel](https://discord.com/channels/784442203187314689/1053086214615466095)!

#### Docker on Windows

Make is not recognized as a native command on Windows machines. As such, you will either need to install make for Windows, or use a Linux Terminal via [WSL2](https://learn.microsoft.com/en-us/windows/wsl/install).

### Visual Studio Code

You can use any code editor, but [VS Code](https://code.visualstudio.com/) is our recommendation due to available extensions. All code that is to be suggested via PR must be formatted correctly using the [formatter linked here](https://marketplace.visualstudio.com/items?itemName=henriblancke.vscode-dbt-formatter).

The extension [dbt Power User](https://marketplace.visualstudio.com/items?itemName=innoverio.vscode-dbt-power-user) is also recommended.



You are now ready to create your first data contribution! Read on for an example contribution guide which includes some dbt basics, or review the [Model Standards](../model-standards/) for insight on how we structure our projects.
