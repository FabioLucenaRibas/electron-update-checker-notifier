**In English**
# UpdateCheckerNotifier
[![downloads](https://badgen.net/npm/dt/electron-update-checker-notifier)](https://npm-stat.com/charts.html?package=electron-update-checker-notifier&from=2023-01-01)
[![npm-version](https://badgen.net/npm/v/electron-update-checker-notifier?icon=npm&label)](https://www.npmjs.com/package/electron-update-checker-notifier)
[![github-tag](https://badgen.net/github/tag/FabioLucenaRibas/electron-update-checker-notifier)](https://github.com/FabioLucenaRibas/electron-update-checker-notifier/tags)
[![license](https://badgen.net/github/license/FabioLucenaRibas/electron-update-checker-notifier)](LICENSE.txt)
[![install size](https://packagephobia.com/badge?p=electron-update-checker-notifier)](https://packagephobia.com/result?p=electron-update-checker-notifier)
[![build](https://github.com/FabioLucenaRibas/electron-update-checker-notifier/workflows/build/badge.svg)](https://github.com/FabioLucenaRibas/electron-update-checker-notifier/actions)
![ts](https://badgen.net/badge/Built%20With/TypeScript/blue)

It's a project that seeks new updates for the app from the GitHub repository and informs the user about these updates. The goal is to keep the user informed about the latest versions of their software and allow for simple and fast updating.

# Functionalities
* Checks the latest version of the app in the Github repository.
* Displays a notification to the user when a new update is available.
* Event management for customizing update checks and notification display.
* Ability to choose the language used for log messages and notifications.

# Language setting
You can choose the language that will be used for log messages and notifications by adding the following option to the updateNotification method call:

```javascript
import { updateCheckerNotifier, Language } from 'electron-update-checker-notifier';

updateCheckerNotifier.language = Language.PT_BR;

updateCheckerNotifier.updateNotification();
```
```javascript
import { UpdateCheckerNotifier, Language } from 'electron-update-checker-notifier';

const notifier = new UpdateCheckerNotifier();

notifier.updateNotification({
  language: Language.PT_BR,
});
```

The currently supported languages are:
* en-US (English - United States)
* pt-BR (Portuguese - Brazil)

# Installation

```bash
npm install electron-update-checker-notifier
```

# Use
To use UpdateCheckerNotifier, you need to import it and create an instance. Then, you can call the updateNotification() method to check if there are updates available for your app.

```javascript
import { UpdateCheckerNotifier } from 'electron-update-checker-notifier';

const notifier = new UpdateCheckerNotifier();
notifier.updateNotification();
```

# Options
You can pass options to the updateNotification() method to customize its behavior.

**repository** (Optional): Your app repository on GitHub. If not specified, it will use the repository defined in your app's package.json file.

**token** (Optional): The access token to the GitHub API.

**debug** (Optional, default: false): Allows checking for updates during development.

**enableNewVersionAvailableDialog** (Optional, default: true): Notifies when there are new versions available, otherwise remains silent.

**enableLatestVersionDialog** (Optional, default: false): Notifies when you are already running the latest version.

**enableErrorDialog** (Optional, default: false): Notifies when an error occurs.

**language** (Optional, default: Language.EN): The language used for log messages and notifications.

**logger** (Optional): The logger. You can pass a logger such as electron-log, winston, or other with the following interfaces: { **info()**, **warn()**, **error()** }. Set to null if you wish to disable logging.

# Events
UpdateCheckerNotifier emits several events that you can listen to for information about the update process.

**checking-for-update**: Emitted when the update check process begins.

**update-available**: Emitted when there is a new version available for download.

**update-not-available**: Emitted when there are no new updates available.

**this-is-last-update**: Emitted when the update check determines that the current version of your app is the last available version.

**error**: Emitted when an error occurs during the update check process.

You can listen to these events as follows:
```javascript
notifier.on('checking-for-update', () => {
  console.log('Checking for updates...');
});

notifier.on('update-available', (info: UpdateInfo) => {
  console.log(`A new version (${info.version}) is available for download!`);
});

notifier.on('update-not-available', (info: UpdateInfo) => {
  console.log('There are no new updates available.');
});

notifier.on('this-is-last-update', (info: UpdateInfo) => {
  console.log('This is the latest update available.: ', info);
});

notifier.on('error', (error: Error) => {
  console.error(`An error has occurred: ${error}`);
});
```

The UpdateInfo object is passed as an argument to the event handler and contains information about the current and latest available version of your application.

# Example
Here is a full example of how to use UpdateCheckerNotifier in an Electron application:
```javascript
import { updateCheckerNotifier, Language } from 'electron-update-checker-notifier';

updateCheckerNotifier.repository = 'user/repo'
updateCheckerNotifier.token = 'my-github-token'
updateCheckerNotifier.debug = true
updateCheckerNotifier.enableNewVersionAvailableDialog = true
updateCheckerNotifier.enableLatestVersionDialog = true
updateCheckerNotifier.enableErrorDialog = true
updateCheckerNotifier.language = Language.PT_BR
updateCheckerNotifier.logger = log

updateCheckerNotifier.updateNotification();
```

```javascript
import { UpdateCheckerNotifier, Language } from 'electron-update-checker-notifier';

const notifier = new UpdateCheckerNotifier();

notifier.updateNotification({
  repository: 'user/repo',
  token: 'my-github-token',
  debug: true,
  enableNewVersionAvailableDialog: true,
  enableLatestVersionDialog: true,
  enableErrorDialog: true,
  language: Language.PT_BR,
  logger: log,
});

notifier.on('update-available', (info: UpdateInfo) => {
  console.log(`A new version (${info.version}) is available for download!`);
});

notifier.on('error', (error: Error) => {
  console.error(`An error has occurred: ${error}`);
});
```

# Contribution
If you want to contribute to this project, follow these steps:

1. Fork the repository
2. Create your branch
3. Commit your changes
4. Push on the branch
5. Create a pull request

# Acknowledgments
I would like to thank the following developers for the work done on the project [electron-update-notifier](https://github.com/ankurk91/electron-update-notifier)

* [ankurk91](https://github.com/ankurk91)
* [pd4d10](https://github.com/pd4d10)

Thank you for your dedication and contribution to the community.

# License
This project is licensed under the MIT license. See the [LICENSE](https://github.com/FabioLucenaRibas/electron-update-checker-notifier/blob/main/LICENSE) file for more details.


**In Portuguese**
# UpdateCheckerNotifier
[![downloads](https://badgen.net/npm/dt/electron-update-checker-notifier)](https://npm-stat.com/charts.html?package=electron-update-checker-notifier&from=2023-01-01)
[![npm-version](https://badgen.net/npm/v/electron-update-checker-notifier?icon=npm&label)](https://www.npmjs.com/package/electron-update-checker-notifier)
[![github-tag](https://badgen.net/github/tag/FabioLucenaRibas/electron-update-checker-notifier)](https://github.com/FabioLucenaRibas/electron-update-checker-notifier/tags)
[![license](https://badgen.net/github/license/FabioLucenaRibas/electron-update-checker-notifier)](LICENSE.txt)
[![install size](https://packagephobia.com/badge?p=electron-update-checker-notifier)](https://packagephobia.com/result?p=electron-update-checker-notifier)
[![build](https://github.com/FabioLucenaRibas/electron-update-checker-notifier/workflows/build/badge.svg)](https://github.com/FabioLucenaRibas/electron-update-checker-notifier/actions)
![ts](https://badgen.net/badge/Built%20With/TypeScript/blue)

?? um projeto que busca novas atualiza????es do aplicativo a partir do reposit??rio do GitHub e notifica o usu??rio sobre essas atualiza????es. O objetivo ?? manter o usu??rio informado sobre as vers??es mais recentes de seu software e possibilitar a atualiza????o de maneira simples e r??pida.

# Funcionalidades
* Verifica a vers??o mais recente do aplicativo no reposit??rio do Github.
* Exibi uma notifica????o para o usu??rio quando uma nova atualiza????o estiver dispon??vel.
* Gerenciamento de eventos para personaliza????o da verifica????o de atualiza????es e exibi????o de notifica????es.
* Possibilidade de escolher o idioma usado para as mensagens de log e notifica????es.

# Configura????o de idioma
Voc?? pode escolher o idioma que ser?? utilizado usado para as mensagens de log e notifica????es adicionando a seguinte op????o ?? chamada do m??todo updateNotification:

```javascript
import { updateCheckerNotifier, Language } from 'electron-update-checker-notifier';

updateCheckerNotifier.language = Language.PT_BR;

updateCheckerNotifier.updateNotification();
```
```javascript
import { UpdateCheckerNotifier, Language } from 'electron-update-checker-notifier';

const notifier = new UpdateCheckerNotifier();

notifier.updateNotification({
  language: Language.PT_BR,
});
```

Os idiomas atualmente suportados s??o:

* en-US (Ingl??s - Estados Unidos)
* pt-BR (Portugu??s - Brasil)


# Instala????o

```bash
npm install electron-update-checker-notifier
```
# Uso

Para usar UpdateCheckerNotifier, voc?? precisa import??-lo e criar uma inst??ncia. Em seguida, voc?? pode chamar o m??todo updateNotification() para verificar se h?? atualiza????es dispon??veis para o seu aplicativo.


```javascript
import { UpdateCheckerNotifier } from 'electron-update-checker-notifier';

const notifier = new UpdateCheckerNotifier();
notifier.updateNotification();
```

# Op????es
Voc?? pode passar op????es para o m??todo updateNotification() para personalizar o comportamento.

**repository** (opcional): O reposit??rio do seu aplicativo no GitHub. Se n??o for especificado, ele usar?? o reposit??rio definido no arquivo package.json do seu aplicativo.

**token** (opcional): O token de acesso ?? API do GitHub.

**debug** (opcional, padr??o: false): Permite verificar atualiza????es durante o desenvolvimento.

**enableNewVersionAvailableDialog** (opcional, padr??o: true): Notifica quando houver novas vers??es dispon??veis, caso contr??rio, permanece silencioso.

**enableLatestVersionDialog** (opcional, padr??o: false): Notifica quando voc?? j?? est?? executando a vers??o mais recente.

**enableErrorDialog** (opcional, padr??o: false): Notifica quando um erro acontecer

**language** (opcional, padr??o: Language.EN): O idioma usado para as mensagens de log e notifica????es.

**logger** (opcional): O registrador. Voc?? pode passar um registrador como electron-log, winston ou outro com as seguintes interfaces: { **info()**, **warn()**, **error()** }. 
Defina como null se voc?? desejar desativar o recurso de log.

# Eventos
UpdateCheckerNotifier emite v??rios eventos que voc?? pode ouvir para obter informa????es sobre o processo de atualiza????o.

**checking-for-update**: Emitido quando o processo de verifica????o de atualiza????o come??a.

**update-available**: Emitido quando h?? uma nova vers??o dispon??vel para download.

**update-not-available**: Emitido quando n??o h?? novas atualiza????es dispon??veis.

**this-is-last-update**: Emitido quando quando a verifica????o de atualiza????o determina que a vers??o atual do seu aplicativo ?? a ??ltima vers??o dispon??vel.

**error**: Emitido quando ocorre um erro durante o processo de verifica????o de atualiza????o.

Voc?? pode ouvir esses eventos da seguinte maneira:

```javascript
notifier.on('checking-for-update', () => {
  console.log('Verificando por atualiza????es...');
});

notifier.on('update-available', (info: UpdateInfo) => {
  console.log(`Uma nova vers??o (${info.version}) est?? dispon??vel para download!`);
});

notifier.on('update-not-available', (info: UpdateInfo) => {
  console.log('N??o h?? novas atualiza????es dispon??veis.');
});

notifier.on('this-is-last-update', (info: UpdateInfo) => {
  console.log('Esta ?? a ??ltima atualiza????o dispon??vel: ', info);
});

notifier.on('error', (error: Error) => {
  console.error(`Ocorreu um erro: ${error}`);
});
```
O objeto **UpdateInfo** ?? passado como um argumento para o manipulador de eventos e cont??m informa????es sobre a vers??o atual e a ??ltima vers??o dispon??vel do seu aplicativo.

# Exemplo
Aqui est?? um exemplo completo de como usar UpdateCheckerNotifier em um aplicativo Electron:

```javascript
import { updateCheckerNotifier, Language } from 'electron-update-checker-notifier';

updateCheckerNotifier.repository = 'user/repo'
updateCheckerNotifier.token = 'my-github-token'
updateCheckerNotifier.debug = true
updateCheckerNotifier.enableNewVersionAvailableDialog = true
updateCheckerNotifier.enableLatestVersionDialog = true
updateCheckerNotifier.enableErrorDialog = true
updateCheckerNotifier.language = Language.PT_BR
updateCheckerNotifier.logger = log

updateCheckerNotifier.updateNotification();
```

```javascript
import { UpdateCheckerNotifier, Language } from 'electron-update-checker-notifier';

const notifier = new UpdateCheckerNotifier();

notifier.updateNotification({
  repository: 'user/repo',
  token: 'my-github-token',
  debug: true,
  enableNewVersionAvailableDialog: true,
  enableLatestVersionDialog: true,
  enableErrorDialog: true,
  language: Language.PT_BR,
  logger: log,
});

notifier.on('update-available', (info: UpdateInfo) => {
  console.log(`Uma nova vers??o (${info.version}) est?? dispon??vel para download!`);
});

notifier.on('error', (error: Error) => {
  console.error(`Ocorreu um erro: ${error}`);
});
```

# Contribui????o
Se voc?? deseja contribuir para este projeto, siga as seguintes etapas:

1. Fa??a um fork do reposit??rio
2. Crie sua branch
3. Commit suas altera????es
4. Push na branch
5. Crie um pull request

# Reconhecimentos
Gostar??a de agradecer aos seguintes desenvolvedores pelo trabalho realizado no projeto [electron-update-notifier](https://github.com/ankurk91/electron-update-notifier):

* [ankurk91](https://github.com/ankurk91)
* [pd4d10](https://github.com/pd4d10)

Obrigado por sua dedica????o e contribui????o com a comunidade.

# Licen??a
Este projeto est?? licenciado sob a licen??a MIT. Veja o arquivo [LICENSE](https://github.com/FabioLucenaRibas/electron-update-checker-notifier/blob/main/LICENSE) para mais detalhes.
