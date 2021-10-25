# Installing the IRIDA uploader

The [irida-uploader](https://github.com/phac-nml/irida-uploader) is the main client for loading sequenced samples
into the COMBAT SARS-CoV-2 Workbench. It can be installed using conda using the following procedure:

## Windows Installation

Download the installer for the latest release from the [Github releases page](https://github.com/phac-nml/irida-uploader/releases). The Windows installer is the file ended in *.exe*, for example, `IRIDA_Uploader_GUI_0.6.2.exe`. After downloading the file double-click on the it to run it and start the installation procedure.

## Linux and MacOS installation

You need to have conda and bioconda installed as per the instructions on the [bioconda webpage](https://bioconda.github.io/user/install.html). Once you have these set up you can create an environment for the uploader with

```bash
conda create -n uploader -y irida-uploader PyQT
```

This will create an environment with both the command line uploader and the GUI version. If you only need the command line uploader, you can leave off the `PyQT` package.

You can now run the GUI uploader with `irida-uploader-gui` and the command line uploader with `irida-uploader`.

## Configuring the connection between the Uploader and the Workbench

The IRIDA uploader connects to the Workbench as a client with a particular ID, secret and associated permissions.

Clients are configured by admin users and via the admin panel of the Workbench. You can find the admin panel by clicking on the word ADMIN on the top right of the Workbench web interface. Below is a picture of part of the Workbench menu bar to illustrate what
it looks like and where to find the link to the ADMIN panel.

![Link to Admin Interface](images/admin_menu.png)

Once you are in the admin panel, follow [these instructions](https://phac-nml.github.io/irida-documentation/user/administrator/#managing-system-clients) to add a new client. The Uploader requires a client that uses Password grant type and is approved for both Read and Write Scope permissions. Take note of the client ID and client secret.

### Configuring the GUI client

When you start the Uploader, you will see this screen:

<figure>
    <img src="/images/irida_uploader_gui1.png" alt="IRIDA Uploader GUI Main Page" width="600" />
    <figcaption>IRIDA Uploader GUI Main Page</figcaption>
</figure>

Click the *Configure Settings* button to configure the client. You will see a screen as below. In this example we have filled in all the fields. Note that the *Parser* field describes how your data is structured. Leave this as "directory", as this mode expects a directory with one (for Nanopore or other single-ended platforms like Ion Torrent) or two (for Illumina) files per sample. You can read more about the parser modes in the "Choose a parser" section in [this documentation](https://irida-uploader.readthedocs.io/en/stable/).

<figure>
    <img src="/images/irida_uploader_gui_client_config_complete.png" alt="IRIDA Uploader GUI Client Config" width="600" />
    <figcaption>IRIDA Uploader GUI Client Config</figcaption>
</figure>

Once you have configured the client, click the *Save and Test Settings* button. You should get a "Connection OK!" message. If you do, click "Accept" to accept the settings and close the settings window.
