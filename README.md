# Custom Livechat Development
## Environment Setup
More information [here](https://developer.rocket.chat/rocket.chat/rocket-chat-environment-setup/mac-osx)

- Install **Node 14.19.3** either [manually](https://nodejs.org/dist/latest-v14.x/) or using a tool like [nvm](https://github.com/creationix/nvm) (recommended)
- Install **Meteor**: https://www.meteor.com/developers/install
- Install **yarn**: https://yarnpkg.com/getting-started/install
- Clone the repository and navigate into the directory

```
git clone https://github.com/HTD-Health/Rocket.Chat.git
cd Rocket.Chat
```

- Run the following commands to navigate to the meteor directory and download the necessary meteor version for Rocket.Chat, as configured in `.meteor/release` file

```
cd apps/meteor
meteor --version
```

- Back in the main directory, install all the packages by simply running

```
yarn
```

- Build and startup your development server by executing

```
yarn build
yarn dev # or yarn dsv if your system has less than 16 gigs of memory
```

When done, you should see the following printed on your terminal and the local server running on http://localhost:3000

## Livechat Customization
After changes in the livechat package, you need to build it again
```
cd packages/livechat
yarn build
```
After launching the rocket chat again, the changes should be visible.

## Docker Image Preparation
> Make sure you have the latest version of [Docker](https://www.docker.com/) installed.

> Remember to build the project and livechat package beforehand using `yarn build`.

> Make sure you have the correct version of node (**14.19.3**).

- Navigate to the meteor directory
```
cd apps/meteor
```
- Build the application and copy the `Dockerfile` and `compose.yml` files to the resulting directory
```
meteor build --server-only --directory /tmp/rc-build
cp .docker/Dockerfile /tmp/rc-build
cp .docker/compose.yml /tmp/rc-build
cd /tmp/rc-build
```
- You need to make sure that the resulting image works properly, so we'll use the `compose.yml` file

```
docker compose up
```

If everything went well and the terminal does not report any errors then the local server should be started on http://localhost:3000.

If you want to change the port on which the application is running, create an `.env` file with an example variable
```
HOST_PORT=8000
```
### Troubleshooting

Official Image Repository: https://github.com/RocketChat/Docker.Official.Image
#### **Bcrypt Error**
If you get errors with `bcrypt` when launching the container in the terminal, follow these steps:

- Download the official built package from the link below, where instead of `${RC_VERSION}` enter rocket chat version. 

    https://releases.rocket.chat/${RC_VERSION}/download

- Extract the `.tar` file and replace the `/npm` directory located in `bundle/programs/server/` with the directory in your resulting `/tmp/rc-build/bundle/programs/server/` directory

- Then in the `compose.yml` file add `platform: linux/x86_64` as below:

```
...

services:
  rocketchat:
    platform: linux/x86_64
    build: .
...
```

After deleting the docker image and re-running the `docker compose up` command. The application should run without errors.


<img src="https://github.com/RocketChat/Rocket.Chat.Artwork/raw/master/Logos/2020/png/logo-horizontal-red.png" data-canonical-src="https://github.com/RocketChat/Rocket.Chat.Artwork/raw/master/Logos/2020/png/logo-horizontal-red.png" width="500" />

<h1 align="center">
  The ultimate Free Open Source Solution for team communications.
</h1>

[Rocket.Chat](https://rocket.chat) is an open-source fully customizable communications platform developed in JavaScript for organizations with high standards of data protection.

We are a MERN based application enabling real-time conversations between colleagues, with other companies or with your customers, regardless of how they connect with you. The result is an increase in productivity and customer satisfaction rates.

Every day, tens of millions of users in over 150 countries and in organizations such as Deutsche Bahn, The US Navy, and Credit Suisse trust [Rocket.Chat](https://rocket.chat) to keep their communications completely private and secure.

- [Review product documentation](https://docs.rocket.chat)
- [Review developer documentation](https://developer.rocket.chat)

Using our self-managed offerings you can deploy Rocket.Chat on your own server, or you can use SaaS Rocket.Chat. We offer support for both community as well as commercial plans.

<img src="https://github.com/RocketChat/Rocket.Chat.Artwork/blob/master/Product%20Images/Welcome%20to%20RC%20(Readme).jpg" data-canonical-src="https://github.com/RocketChat/Rocket.Chat.Artwork/blob/master/Product%20Images/Welcome%20to%20RC%20(Readme).jpg" width="919" height="511" />

## Cloud Hosted Rocket.Chat

https://cloud.rocket.chat/trial

## Local development

### Prerequisites

You can follow these instructions to setup a dev environment:

- Install **Node 14.x (LTS)** either [manually](https://nodejs.org/dist/latest-v14.x/) or using a tool like [nvm](https://github.com/creationix/nvm) (recommended)
- Install **Meteor**: https://www.meteor.com/developers/install
- Install **yarn**: https://yarnpkg.com/getting-started/install
- Clone this repo: `git clone https://github.com/RocketChat/Rocket.Chat.git`
- Run `yarn` to install dependencies

### Starting Rocket.Chat

```
yarn dsv
```

After initialized, you can access the server at http://localhost:3000

### Starting Rocket.Chat in microservices mode

```
yarn turbo run ms
```

After initialized, you can access the server at http://localhost:4000

## Installation

Please see the [requirements documentation](https://docs.rocket.chat/installing-and-updating/minimum-requirements-for-using-rocket.chat) for system requirements and more information about supported operating systems.
Please refer to [Install Rocket.Chat](https://rocket.chat/install) to install your Rocket.Chat instance.

## Feature Request

[Rocket.Chat/feature-requests](https://github.com/RocketChat/feature-requests) is used to track Rocket.Chat feature requests and discussions. Click [here](https://github.com/RocketChat/feature-requests/issues/new?template=feature_request.md) to open a new feature request. [Feature Request Forums](https://forums.rocket.chat/c/feature-requests/8) stores the historical archives of old feature requests (up to 2018).

## Community

Join thousands of members worldwide in our [community server](https://open.rocket.chat).
Join [#Support](https://open.rocket.chat/channel/support) for help from our community with general Rocket.Chat questions.
Join [#Dev](https://open.rocket.chat/channel/dev) for needing help from the community to develop new features.
Talk with Rocket.Chat's leadership at the [Community Open Call](https://www.youtube.com/playlist?list=PLee3gqXJQrFVaxryc0OKTKc92yqQX9U-5), held monthly. Join us for [the next Community Open Call](https://app.livestorm.co/rocket-chat/community-open-call?type=detailed).

## Contributions

Rocket.Chat is an open source project and we are very happy to accept community contributions. Please refer to the [How can I help?](https://docs.rocket.chat/contributors/how-can-i-help) for more details.

## Credits

- Emoji provided graciously by [JoyPixels](https://www.joypixels.com).
- Testing with [BrowserStack](https://www.browserstack.com).
- Translations done with [LingoHub](https://lingohub.com).

## Mobile Apps

In addition to the web interface, you can also download Rocket.Chat clients for:

[![Rocket.Chat on Apple App Store](https://user-images.githubusercontent.com/551004/29770691-a2082ff4-8bc6-11e7-89a6-964cd405ea8e.png)](https://itunes.apple.com/us/app/rocket-chat/id1148741252?mt=8) [![Rocket.Chat on Google Play](https://user-images.githubusercontent.com/551004/29770692-a20975c6-8bc6-11e7-8ab0-1cde275496e0.png)](https://play.google.com/store/apps/details?id=chat.rocket.android) [![](https://user-images.githubusercontent.com/551004/48210349-50649480-e35e-11e8-97d9-74a4331faf3a.png)](https://f-droid.org/en/packages/chat.rocket.android)

## Learn More

- [API](https://developer.rocket.chat/reference/api)
- [See who's using Rocket.Chat](https://rocket.chat/customer-stories)

## Become a Rocketeer

We're hiring developers, support people, and product managers all the time. Please check our [jobs page](https://rocket.chat/jobs).

## Get the Latest News

- [Twitter](https://twitter.com/RocketChat)
- [Blog](https://rocket.chat/blog)
- [Facebook](https://www.facebook.com/RocketChatApp)
- [LinkedIn](https://www.linkedin.com/company/rocket-chat)
- [Youtube](https://www.youtube.com/channel/UCin9nv7mUjoqrRiwrzS5UVQ)
- [Email Newsletter](https://rocket.chat/newsletter)

Any other questions, reach out to us at [our website](https://rocket.chat/contact) or you can email us directly at [contact@rocket.chat](mailto:contact@rocket.chat). We’d be happy to help!
