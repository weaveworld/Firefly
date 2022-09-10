# **Firefly** -- *Testing at ease*

`Firefly` is a testing framework for Web applications.

- **Descriptions and Tests** can be combined to produce a **feature map** for the application.
- Testable descriptions can be given in short [fragment](doc/1_sources.md#fragments) files, using a [simplified HTML format](doc/1_sources.md#simplified-html-format).
- Executable steps to test application features are given in **JavaScript/ES** [code](doc/1_sources.md#code).
- An extensive **Firefly wrapper** around the [Selenium framework](https://www.selenium.dev/documentation/webdriver/) helps to simplify writing tests, even for highly dynamic Web pages.
- [Result](doc/4_result.md) data can be easily processed.

## Testing

Firefly can be run from docker.
  - An example is [Testing Spring's example PetClinic application](https://github.com/weaveworld/ff-spring-petclinic)

There are two Firefly docker images:
  - [weaveworld/firefly-desktop](https://hub.docker.com/r/weaveworld/firefly-desktop) - A complete Ubuntu *Desktop* with the Firefox, Chrome and Edge *browsers*, the Selenium *drivers* and the Selenium *Server*, and also contains the **Firefly** environment. 
  - [weaveworld/firefly](https://hub.docker.com/r/weaveworld/firefly) - An executable Firefly environment that can use other remote Selenium hosts, for example [Selenium images](https://github.com/SeleniumHQ/docker-selenium#standalone) or the [weaveworld/selenium](https://github.com/weaveworld/ubuntu-desktop#selenium-weaveworldselenium) image that contains the Firefox, Chrome, Edge *browsers* and the Selenium *drivers* and *Server*.

