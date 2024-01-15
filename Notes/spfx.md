# SPFX

## Project-creation

> [Shareoint Framework](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-development-environment)

```powershell
yo @microsoft/sharepoint
```

## Fast-serve

> [Fast-Serve-Github](https://github.com/s-KaiNet/spfx-fast-serve)

1; First time install

```powershell
npm install spfx-fast-serve -g
```

2; Open a command line in the folder with your sharepoint framework solution that you want to install it on

3; Run ``` spfx-fast-serve ```

4; Run ``` npm install ```

5; Use ``` npm run serve ``` as your usual command to start your Sharepoint Framework solution faster from now on

## Fluent UI

> [FluentUI Documentation](https://react.fluentui.dev/?path=/docs/concepts-developer-quick-start--page)

```powershell
yarn add @fluentui/react-components
```

or for node

```powershell
npm install yarn add @fluentui/react-components
```

Place a ``` <FluentProvider /> ``` in the root of your app

```typescript
import React from 'react';
import ReactDOM from 'react-dom';
import { FluentProvider, teamsLightTheme } from '@fluentui/react-components';

import App from './App';

ReactDOM.render(
  <FluentProvider theme={teamsLightTheme}>
    <App />
  </FluentProvider>,
  document.getElementById('root'),
);
```
