deepstream.io: The Open Realtime Server deepstream is a new type of server that syncs data and sends events across millions of clients Quick links to useful resources on getting started: Installing deepstream Getting started Tutorials Documentation Deploying on AWS Community Links Slack Twitter Stack Overflow Development Guide Deepstream development is a great way for you to go into depth about building performant nodeJS applications, and contributions are always welcome with lots of ❤ Contributing to deepstream.io is as simple as: Downloading nodeJS (4+) Cloning the repo Run npm i / yarn install to install dependencies Make your changes / Add a test Run npm t to see if the unit tests all pass Run sh ./scripts/run-e2e.sh if your changes are quite big. But otherwise CI can take care of that for you ;) For power users who want to make sure the binary works, you can run sh scripts/package.sh true. Youll need to download the usual node-gyp build environment for this to work and we only support the latest LTS version to compile. This step is usually not needed though unless your modifying resource files or changing dependencies. Post release sanity test for linux distributions: access a linux machine copy over the sanity test using: curl -O https://raw.githubusercontent.com/deepstreamIO/deepstream.io/master/scripts/sanity-test.sh depending on your distribution, run debian/ubuntu: bash sanity-test.sh deb centos/aws: bash sanity-test.sh rpm any linux distro: bash sanity-test.sh tar