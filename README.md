# Sobre o projeto

Projeto de testes de testes automatizados com Robot Framework integrado ao Tox e Robotidy.

## O que é o Tox?

[Tox][WhatIsTox] é uma ferramenta genérica de linha de comando de teste e gerenciamento de ```virtualenv```

## O que é o Robotidy?

[Robotidy][RobotidyIntroduction] é uma ferramenta para autoformatação de código para o Robot Framework.

É descendente do pacote [robot.tidy][RobotidyRobotFramework] interno do Robot Framework.

## Instalação no Windows

1. Instale o [Python][Python] com o [pip][pip].
2. Instale o [Android Studio][AndroidStudio].
3. Clone este projeto.
4. Instale o [Tox][ToxInstall] ```pip install tox```.
5. Execute o comando ```rfbrowser init``` para instalar as dependencias do robotframework-browser.
6. Instale o [NodeJS][NodeJS] para utilizar o Appium.
7. Instale o [Appium 2.0][Appium2.0] ```npm install appium-installer -g```.
8. Instale o Appium Server e o driver uiautomator2 para execução dos testes mobile usando o ```appium-installer```

- Tenha o Java JDK11 ou superior instalado e configurado para utilizar o Appium Desktop e o Android Studio.

- Configure a variável `%ANDROID_HOME%` do Android Studio em `%userprofile%\AppData\local\Android\Sdk` e adicione os diretórios `%ANDROID_HOME%\platform-tools`, `%ANDROID_HOME%\tools`, `%ANDROID_HOME%\tools\bin`, `%ANDROID_HOME\tools\lib` no path do seu sistema.

- Use o comando `appium` para iniciar o Appium Server.

No arquivo tox.ini estão configurados as variáveis locais para executar os testes de serviços, mobile e web. Elas estão identificadas com o `-local` no final.


### Exemplo de execução do testes

```bash
tox run-parallel -p 3 -e servicetests-local -- .
```

```bash
tox run-parallel -p 3 -e mobiletests-local -- .
```

```bash
tox run-parallel -p 3 -e webtests-local -- .
```

- NOTA: Caso não queira executar os testes em paralelo, remova o argumento ```run-parallel``` na execução.

Você pode utilizar o argumento ```-i <FEATURE_TAG>``` para executar apenas os testes com as tags específicas. Lembre-se de passar as variáveis do tox que contém as TAGs no argumento de execução.

### Exemplo de execução por TAG

```bash
tox run-parallel -p 3 -e mobiletests-local -- -i home .
```

Para executar os testes Web sem o modo headless, adicione o argumento ```-v HEADLESS:False``` na linha de comando.

### Exemplo de execução dos testes web com o modo HEADLESS desabilitado

```bash
tox run-parallel -p 3 -e webtests -- -v HEADLESS:False .
```

[WhatIsTox]: https://tox.wiki/en/latest/#what-is-tox
[RobotidyIntroduction]: https://robotidy.readthedocs.io/en/stable/#introduction
[RobotidyRobotFramework]: https://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#tidy
[Python]: https://www.python.org/
[pip]: https://pip.pypa.io
[ToxInstall]: https://tox.wiki/en/latest/installation.html
[Appium2.0]: https://appium.io/
[AndroidStudio]: https://developer.android.com/studio
[NodeJS]: https://nodejs.org/en/