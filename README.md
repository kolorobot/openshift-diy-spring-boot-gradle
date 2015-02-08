# Prerequisite

Before we can start building the application, we need to have an OpenShift free account and client tools installed.

# Step 1: Create DIY application

To create an application using client tools, type the following command:

    rhc app create <app-name> diy-0.1

This command creates an application *<app-name>* using *DIY* cartridge and clones the repository to *<app-name>* directory.

# Step 2: Delete Template Application Source code

OpenShift creates a template project that can be freely removed:

    git rm -rf .openshift README.md diy misc

Commit the changes:

    git commit -am "Removed template application source code"

# Step 3: Pull Source code from GitHub

    git remote add upstream https://github.com/kolorobot/openshift-diy-spring-boot-gradle.git
    git pull -s recursive -X theirs upstream master

# Step 4: Push changes

The basic template is ready to be pushed to OpenShift:

	git push

The initial deployment (build and application startup) will take some time (up to several minutes). Subsequent deployments are a bit faster:

    remote: BUILD SUCCESSFUL
    remote: Starting DIY cartridge
    Started DemoApplication in 15.284 seconds (JVM running for 17.402)

You can now browse to: `http://<app-name>.rhcloud.com/manage/health` and you should see:

	{
		"status": "UP",
	}
