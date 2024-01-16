# SPFX

## Project-creation

> [Shareoint Framework](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-development-environment)

```ps
yo @microsoft/sharepoint
```

## Fast-serve

> [Fast-Serve-Github](https://github.com/s-KaiNet/spfx-fast-serve)

1; First time install

```ps
npm install spfx-fast-serve -g
```

2; Open a command line in the folder with your sharepoint framework solution that you want to install it on

3; Run ``` spfx-fast-serve ```

4; Run ``` npm install ```

5; Use ``` npm run serve ``` as your usual command to start your Sharepoint Framework solution faster from now on

## Fluent UI

> [FluentUI Documentation](https://react.fluentui.dev/?path=/docs/concepts-developer-quick-start--page)

```ps
npm i @fluentui/react-components
```

Create a `"Yourwebpartname"Provider.tsx` file and Import your fluent provider

```ts
import * as React from 'react';
import {
  FluentProvider,
  teamsDarkTheme,
  teamsHighContrastTheme,
  teamsLightTheme,
  Theme,
  tokens,
} from '@fluentui/react-components';
// eslint-disable-next-line @typescript-eslint/no-unused-vars
import { createV9Theme } from "@fluentui/react-migration-v8-v9"
import { IPracticeProjProps } from './IPracticeProjProps';
import PracticeProj from './PracticeProj';

export const PracticeProjProvider: React.FunctionComponent<IPracticeProjProps > = (props: React.PropsWithChildren<IPracticeProjProps >) => {
  const { themeString , theme, hasTeamsContext  } = props;

  const setTheme = React.useCallback(():Partial<Theme> => {
      if (hasTeamsContext){
       return  themeString === "dark"
            ? teamsDarkTheme
            : themeString === "contrast"
            ? teamsHighContrastTheme
            : {
                ...teamsLightTheme,
                colorNeutralBackground3: "#eeeeee",
              }
      } else {
           return createV9Theme(theme)
        }
    
  }, [themeString, theme, hasTeamsContext, createV9Theme]);

  return (
    <>
      <FluentProvider
        theme={
          setTheme()
        }
        style={{ background: tokens.colorNeutralBackground3 }}
      >
        <PracticeProj {...props} />
      </FluentProvider>

    </>
  );
};
```

make sure the properties in your props are correct as well

```ts
import { Theme } from "@fluentui/react";

export interface IPracticeProjProps {
  ProjektDef: string;
  PreferedView: string;
  isDarkTheme: boolean;
  environmentMessage: string;
  hasTeamsContext: boolean;
  userDisplayName: string;
  onConfigure: () => void;
  isConfigured: boolean;
  themeString?: string;
  theme: Theme;
}
```

or to make it less complicated you can also just Place a ``` <FluentProvider /> ``` in the root of your app. Although with bigger applications this is less practical

```ts
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

## Teams Toolkit

```ps
npm install -g @microsoft/teamsfx-cli
```
