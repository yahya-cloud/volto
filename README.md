# Volto

<img align="right" width="300" alt="Volto logo png" src="./logos/VoltoLogoEra2.png#gh-light-mode-only" />
<img align="right" width="300" alt="Volto logo png" src="./logos/VoltoLogoEra2-dark-mode.png#gh-dark-mode-only" />

[![NPM](https://img.shields.io/npm/v/@plone/volto.svg)](https://www.npmjs.com/package/@plone/volto)
[![Build Status Core](https://github.com/plone/volto/actions/workflows/core.yml/badge.svg)](https://github.com/plone/volto/actions)
[![Build Status Docs](https://github.com/plone/volto/actions/workflows/docs.yml/badge.svg)](https://github.com/plone/volto/actions)

## Introduction

[Volto](https://github.com/plone/volto) is a ReactJS-based frontend for the [Plone](https://plone.org) Content Management System. It will become the default UI for the upcoming Plone 6 release.

[Plone](https://plone.org) is a CMS built on Python with more than 20 years of history and experience.

Plone has very interesting features that appeal to developers and users alike,
such as customizable content types, hierarchical URL object traversing and a
sophisticated content workflow powered by a granular permissions model. This
allows you to build anything from simple websites to enterprise-grade
intranets.

Volto exposes all these features and communicates with Plone via its [REST API](https://github.com/plone/plone.restapi).
Volto has the ability of being easily extensible, themeable, and customizable.

It features the Pastanaga editor, a modern block-based content layout editor. It is extensible and customizable, so you can adapt the default blocks provided to match your requirements, or build new ones to cover them.

Volto is extensible using add-ons.
You can build your own or choose from the community released ones:

- [Volto Add-ons in NPM](https://www.npmjs.com/search?q=keywords%3Avolto-addon%2Cvolto)
- [Volto Awesome](https://github.com/collective/awesome-volto)

## Demo

You can try a Volto online demo in [https://6.demo.plone.org/](https://6.demo.plone.org/)

### Try the demo locally

If you want to give Volto a quick try and you have [Docker](https://www.docker.com/get-started) installed in your computer, bootstrap the demo using `docker-compose`:

```shell
git clone https://github.com/plone/volto.git
cd volto
docker-compose up
```

Go to [http://localhost:3000](http://localhost:3000) in your browser.

## Quick Start

First get all the requirements installed on your system.

### Prerequisites

- [Node.js LTS (16.x)](https://nodejs.org/)
- [Python 3.8.x](https://python.org/) or
- [Docker](https://www.docker.com/get-started) (if using the Plone docker images)

### Create a Volto project using the generator

Create a new Volto project by using the `@plone/generator-volto` utility.

It will bootstrap a Volto project in a folder of your choice with all the required
boilerplate to start customizing your Volto site.

```shell
npm install -g yo @plone/generator-volto
yo @plone/volto
```
> 💡 **HINT** In case the `npm install` command throws an error, which would be most likely due to a permissions issue in your home directory, you will need to reclaim ownership of the `.npm` directory.
You can do so by executing

```shell
sudo chown -R $(whoami) ~/.npm
```

Follow the prompt's questions, providing `myvoltoproject` as the project name.
When it finishes, change your working directory:

```shell
cd myvoltoproject
```
### Bootstrap the Plone API backend

You can bootstrap a ready Docker Plone container with all the dependencies and ready for Volto use. We recommend to use the Plone docker builds based in `pip` [plone/plone-backend](https://github.com/plone/plone-backend) image:

```shell
docker run -it --rm --name=plone -p 8080:8080 -e SITE=Plone -e ADDONS="plone.restapi==8.18.0 plone.app.iterate==4.0.2 plone.rest==2.0.0a1 plone.app.vocabularies==4.3.0 plone.volto==3.1.0a7" -e PROFILES="plone.volto:default-homepage" plone/plone-backend
```

or as an alternative if you have experience with Plone and you have all the
dependencies installed on your system, you can use the supplied convenience buildout in the
`api` folder by issuing the command:

```shell
make build-backend
```

#### Recommended Plone version

Volto is Plone 6 default UI, so it will work for all Plone 6 released versions.

For the Plone 5 series latest released version (with Python 3) and above is recommended (at the time of writing 5.2.6).

The following KGS (or above) are also recommended, for any Plone version used.

#### KGS (known good set of versions) for backend packages

Volto always works best with latest versions of the "Frontend stack" or at least the recommended ones (in parenthesis) which are:

- plone.restapi (8.21.2)
- plone.rest (2.0.0a3)
- plone.volto (4.0.0a3)

and the following core packages since some features require up to date versions:

- plone.app.iterate (4.0.2)
- plone.app.vocabularies (4.3.0)

### Start Volto

```shell
yarn start
```

### Browsing

Go to [http://localhost:3000](http://localhost:3000) in your browser.

## Volto in Production

Volto is actively developed since 2017 and used in production since 2018 on the following websites:

- [VHS Ehrenamtsportal](https://vhs-ehrenamtsportal.de) (Website to help volunteers that help refugees for the [German Adult Education Association](https://www.dvv-vhs.de/en/home/), developed by [kitconcept GmbH](https://kitconcept.com), 2018)
- [Zeelandia](https://zeelandia.de) (Corporate website for one of the leading backery ingrediences manufactors in Germany, developed by [kitconcept GmbH](https://kitconcept.com), 2019)
- [Excellence at Humboldt-Universität zu Berlin](https://www.alles-beginnt-mit-einer-frage.de) (Website for the excellence initiative of the [Humboldt University Berlin](https://hu-berlin.de), developed by [kitconcept GmbH](https://kitconcept.com), 2019)
- [Forest Information System for Europe](https://forest.eea.europa.eu) (Thematic website focusing on European forests, developed by [Eau de Web](https://www.eaudeweb.ro), 2019)
- [Industrial Emissions portal for Europe](https://industry.eea.europa.eu) (Thematic website focusing on European industrial emissions, developed by [Eau de Web](https://www.eaudeweb.ro), 2020)
- [Energy Climate Union portal for Europe](https://climate-energy.eea.europa.eu/) (Thematic website focusing on European strides towards mitigating climate change, developed by [Eau de Web](https://www.eaudeweb.ro), 2020)
- [Talke Carrer Website](https://karriere.talke.com/) (Carrer website for [Talke](https://www.talke.com), one of the leading a chemical and petrochemical logistics companies in Germany, developed by [kitconcept GmbH](https://kitconcept.com), 2020)
- [Stradanove](http://www.stradanove.it/) (Website of the Department of Youth Policies of the Municipality of Modena, developed by [RedTurtle](https://redturtle.it), 2020)
- [VisitModena](https://www.visitmodena.it/) (Tourist website of the Municipality of Modena, developed by [RedTurtle](https://redturtle.it), 2020)
- [Study guide at University of Jyväskylä](https://studyguide.jyu.fi/2020/) (Static website where [Volto is used as a headless CMS for authoring additional content](https://tech.blog.jyu.fi/2020/06/plone-volto-hasura-gatsbyjs-mashup/), 2020)
- [Nuova Voce Ecologista](https://nuovavoceecologista.it) (Website of Nuova Voce Ecologista, an Italian green Party, 2020)
- [BISE](https://biodiversity.europa.eu) (Biodiversity Information System for Europe, developed by [Eau de Web](https://www.eaudeweb.ro), 2019)
- [MEDICE Webseite](https://medice.com/de-de) (Website for MEDICE Arzneimittel Pütter GmbH & Co. KG), developed by [Werkbank GmbH](https://werkbank.de/), 2020)
- [Jobfamilie MEDICE](https://jobfamilie.medice.de/de) (Carrer website for MEDICE Arzneimittel Pütter GmbH & Co. KG), developed by [Werkbank GmbH](https://werkbank.de/), 2020)
- [Baccanale Imola](https://www.baccanaleimola.it) (Baccanale is a food fair that happens every year in Imola, Italy. Developed by [RedTurtle](https://redturtle.it), 2020)
- [ResOU](https://resou.osaka-u.ac.jp) (ResOU is introducing official researched releases by the University of Osaka, Japan. Developed by [CMScom](https://www.cmscom.jp), 2020)
- [Humboldt Labor](https://www.humboldt-labor.de/) (The Humboldt Lab is a website where the Humboldt University Berlin presents its latest reaseach projects and findings. Developed by [WLDX](https://wldx.de/) and [kitconcept GmbH](https://kitconcept.com), 2020)
- [Osaka University](https://www.osaka-u.ac.jp/en) (Osaka University is considered one of the most prestigious universities in Japan. Developed by [CMScom](https://www.cmscom.jp), 2021)
- [Comune di Modena](https://www.comune.modena.it/) (Website of the Municipality of Modena. Developed by [RedTurtle](https://redturtle.it), 2020)
- [Comune di Camposanto](https://www.comune.camposanto.mo.it/) (Website of the Municipality of Camposanto. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Comune di Cantagallo](https://www.comune.cantagallo.po.it/) (Website of the Municipality of Cantagallo. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Comune di Vernio](https://www.comune.vernio.po.it/) (Website of the Municipality of Vernio. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Unione dei Comuni della Val Bisenzio](https://www.bisenzio.it/) (Website of the Municipality union of Val Bisenzio. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Comune di Vaiano](https://www.comune.vaiano.po.it/) (Website of the Municipality of Vaiano. Developed by [RedTurtle](https://redturtle.it), 2021)
- [ASP Area Nord](https://www.aspareanord.it/) (Website of the Public company of personal services of the Modena municipalities in the north area. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Comune di San Possidonio](https://www.comune.sanpossidonio.mo.it/) (Website of the Municipality of San Possidonio. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Comune di Mirandola](https://comune.mirandola.mo.it/) (Website of the Municipality of Mirandola. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Comune di Medolla](http://www.comune.medolla.mo.it/) (Website of the Municipality of Medolla. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Camera di Commercio dell'Umbria](https://www.umbria.camcom.it) (Website Chamber of Commerce of Umbria. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Biblioteche Pianura Est](https://bibest.it) (Website of the Associated libraries of eastern plain. Developed by [RedTurtle](https://redturtle.it), 2021)
- [Camera di Commercio di Reggio Emilia](https://www.re.camcom.gov.it/) (Website Chamber of Commerce of Reggio Emilia. Developed by [RedTurtle](https://redturtle.it), 2021)
- [RawMaterial](https://rawmaterial.it/en) (Company's website. Developed by [RawMaterial](https://rawmaterial.it/en), 2021)
- [WISE-Freshwater](https://water.europa.eu/freshwater) (WISE-Freshwater, the Freshwater Information System for Europe. Developed by [Eau de web](https://eaudeweb.ro) for the European Environmental Agency, 2021)
- [EEA-IMSv4](https://www.eea.europa.eu/ims) (EEA Indicator Management System v4. Developed by [Eau de web](https://eaudeweb.ro) for the European Environmental Agency, 2021)
- [Memori](https://memori.ai/en) (Corporate website for Memori, startup specialising in technologies applied to the experience of memory through the development of Artificial Intelligences. Developed by [RawMaterial](https://rawmaterial.it/en), 2021)
- [TwinCreator](https://twincreator.com/en) (TwinCreator allows you to design and train multiple AI’s through simple conversation through NLP. Developed by [RawMaterial](https://rawmaterial.it/en), 2021)
- [MemoryTwin](https://memorytwin.com/en) (Product website, MemoryTwin allows you to create your personal artificial intelligence, able to remember and speak. Developed by [RawMaterial](https://rawmaterial.it/en), 2022)

Please create a new [issue](https://github.com/plone/volto/issues/new) or [pull request](https://github.com/plone/volto/pulls) to add your Volto-site here!

## Documentation

You can find the latest (in-progress) documentation in [https://6.dev-docs.plone.org/](https://6.dev-docs.plone.org/volto/index.html)

## Training

On the [Plone Trainings Website](https://training.plone.org) you'll find
Volto-dedicated open training materials, plus React and other
JavaScript-centered trainings.

- [Mastering Plone 6 Development](https://training.plone.org/5/mastering-plone/)
  The comprehensive training on Plone 6 with best practice tips for developers and integrators.
- [Volto](https://training.plone.org/5/volto/index.html)
  A detailed training on how to create your own website using Volto frontend.
- [Volto Hands-On](https://training.plone.org/5/voltohandson/index.html)
- [Volto Add-ons Development](https://training.plone.org/5/voltoaddons/index.html)
- [Plone Deployment](https://training.plone.org/5/plone-deployment/index.html)
- [React](https://training.plone.org/5/react/index.html)
- [JavaScript For Plone Developers](https://training.plone.org/5/javascript/index.html)

## Talks

### Plone Conference Ferrara 2019

[Víctor Fernández de Alba - Plone Beyond 2020: Jump into Volto today!](https://www.youtube.com/watch?v=8QrGOgXo1Js&list=PLGN9BI-OAQkQD9HliElIk9pe-8O_Y6S04&index=16&t=0s)

[Rob Gietema - How to create your own Volto site!](https://www.youtube.com/watch?v=3QLN8tsjjf4&list=PLGN9BI-OAQkQD9HliElIk9pe-8O_Y6S04&index=11&t=0s)

[Timo Stollenwerk - On the Road - Plone 6 and Beyond](https://www.youtube.com/watch?v=suXVdfYV2kA&list=PLGN9BI-OAQkQD9HliElIk9pe-8O_Y6S04&index=14&t=0s)

[Rodrigo Ferreira de Souza - Data migration to Plone 5.2 and Volto](https://www.youtube.com/watch?v=kb9SEsnllqE&list=PLGN9BI-OAQkQD9HliElIk9pe-8O_Y6S04&index=49&t=0s)

[Nicola Zambello - A Volto story: building a website by prototyping](https://www.youtube.com/watch?v=xtxJURICkWc&list=PLGN9BI-OAQkQD9HliElIk9pe-8O_Y6S04&index=17&t=0s)

[Luca Pisani - Plone and React.js: An interview to Volto](https://www.youtube.com/watch?v=JZFUOG843no&list=PLGN9BI-OAQkQD9HliElIk9pe-8O_Y6S04&index=26&t=0s)

### Plone Conference Tokyo 2018

[Rob Gietema - Volto](https://2018.ploneconf.org/talks/plone-react)

[Rob Gietema / Víctor Fernández de Alba - Volto Extensibility Story](https://2018.ploneconf.org/talks/plone-react-extensibility-story)

[Víctor Fernández de Alba - Theming Volto](https://2018.ploneconf.org/talks/theming-plone-react)

[Timo Stollenwerk / Víctor Fernández de Alba / Ramon Navarro - Volto Case Studies](https://2018.ploneconf.org/talks/plone-react-case-studies-when-stability-and-security-meet-speed-and-a-modern-user-interface)

[Timo Stollenwerk - Reinventing Plone, Roadmap to the Modern Web](https://2018.ploneconf.org/talks/reinventing-plone-roadmap-to-the-modern-web)

## Node Support

- Node 16: Supported since Volto 14
- Node 14: Supported since Volto 8.8.0
- Node 12: Supported since Volto 4
- Node 10: Deprecated from Volto 13 onwards. It was supported since Volto 1 (and its predecessor "plone-react")

## Browser support

Volto works well with any modern (evergreen) browser, including their mobile
flavors: Chrome, Firefox, Safari, Edge.

We do not guarantee that deprecated browsers (e.g., Internet Explorer 11) are supported by Volto. Although proven possible, it's too great an effort to maintain. It is left to the integrator to provide support for it.

## Upgrades

You can find the upgrade guide here: https://6.dev-docs.plone.org/volto/upgrade-guide/index.html

## Volto Development

For Volto development you need all the requirements already mentioned on the
[Quick Start](#quick-start) section.

### Checkout the Volto repository

```shell
git clone https://github.com/plone/volto.git
```

### Install dependencies

```shell
yarn
```

### Install Plone backend

Either using a Docker command:

```shell
docker run -it --rm --name=backend -p 8080:8080 -e SITE=Plone -e ADDONS="plone.restapi==8.21.2 plone.app.iterate==4.0.2 plone.rest==2.0.0a3 plone.app.vocabularies==4.3.0 plone.volto==4.0.0a3" -e PROFILES="plone.volto:default-homepage" plone/plone-backend
```

or using the convenience makefile command:

```shell
make start-backend-docker
```

or running Plone on your machine (advanced), additional dependencies might be
required, only for Plone experienced integrators/developers. Check the [Plone
Installation Documentation](https://docs.plone.org/manage/installing/installation.html).

```shell
make build-backend
```

### Run frontend

Either using a Docker command:

```shell
docker run -it --rm --name=volto --link backend -p 3000:3000 -e RAZZLE_INTERNAL_API_PATH=http://backend:8080/Plone -e RAZZLE_DEV_PROXY_API_PATH=http://backend:8080/Plone plone/plone-frontend:latest
```

or using the convenience makefile command:

```shell
make start-frontend-docker
```

or from the local repository code:

```shell
yarn && yarn start
```

### Browsing

Browse to [http://localhost:3000](http://localhost:3000) in your browser.

### Testing

```shell
yarn test
```

### Releasing

For ease the release process, we use `release-it` utility that helps with the process.

https://www.npmjs.com/package/release-it

For using it and start a release you need to fulfill the requirements:

- Have permissions to push on master branch
- Have permissions on the @plone org on npmjs.com
- Have a environment variable (`GITHUB_TOKEN`) with a GitHub personal token with permissions to
  write the Volto Release page on GitHub (https://www.npmjs.com/package/release-it#github-releases)

Then the command for release:

```shell
yarn release
```

a dry-release command for testing the output is also available:

```shell
yarn dry-release
```

and alpha release can also be cut using:

```shell
yarn release-alpha
```

### Acceptance testing

Volto uses [Cypress](https://www.cypress.io/) for browser-based acceptance testing.

There are a number of fixtures available covering all the configuration use cases. These fixtures have both a specific backend and frontend configuration setup and a related set of tests. The CI infrastructure runs them all automatically on every push to a branch or PR.

The tests can be run in headless mode (same as the CI does), or within the Cypress user interface. The latter is the one that you run under development.

### How to run acceptance tests locally (during development)

When writing new acceptance tests, you usually want to minimize the time it takes to run the tests, while also being able to debug or inspect what's going on.

To do so, start three individual terminal sessions for running the Plone backend, the Volto frontend, and the acceptance tests.

1.  Run the backend fixture
    ```shell
    make test-acceptance-server
    ```
2.  Run the frontend fixture
    ```shell
    yarn cypress:start-frontend
    ```
3.  Run the Cypress tests for that fixture
    ```shell
    yarn cypress:open
    ```

Available fixtures:

- Core (core or not special naming in the test commands)
- Multilingual (multilingual)
- Working Copy (workingCopy)
- Core Sandbox (coresandbox)

There are convenience commands for each of these fixtures. See `package.json` or `.github` CI setup for more information.

#### Writing new acceptance tests

Go to the `cypress/tests` folder to see existing tests. There is a directory per fixture.
This directory is hot reloaded with your changes as you write the tests. For more information on how to write Cypress tests:

    https://docs.cypress.io

## Translations

If you would like contribute to translate Volto into several languages, please, read the [Internationalization (i18n) guide](https://docs.voltocms.com/customizing/i18n/).

## Contributors

<a href="https://github.com/plone/volto/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=plone/volto" />
</a>

## Alternative backends

Volto also supports other APIs like [Guillotina](https://guillotina.io/), a
Python resource management system, inspired by Plone and using the same basic
concepts like traversal, content types, and permissions model.

Last but not least, it also supports a [Volto Node.js-based backend reference](https://github.com/plone/volto-reference-backend) API implementation that
demos how other systems could also use Volto to display and create content
through it.

### Run a Guillotina backend

*Disclaimer:* Guillotina doesn't support the full API/features that Plone provides. Contributors are welcome.

```shell
docker-compose -f g-api/docker-compose.yml up -d
```

or using the convenience makefile command:

```shell
make start-backend-docker-guillotina
```

### Running the acceptance tests with Guillotina backend

If you want to use Guillotina as a backend to run the tests you should run:

```shell
yarn ci:start-api-plone-guillotina
```

## License

MIT License. Copyrights hold the [Plone Foundation](https://plone.org/foundation).

See [LICENSE.md](LICENSE.md) for details.
