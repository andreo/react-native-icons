# React Native Icons

[![NPM](https://nodei.co/npm/react-native-icons.png?downloads=true&downloadRank=true)](https://nodei.co/npm/react-native-icons/)

[![Join the chat at https://gitter.im/corymsmith/react-native-icons](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/corymsmith/react-native-icons?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

A React Native wrapper on top of [https://github.com/PrideChung/FontAwesomeKit].

Currently we support **5** different icon fonts and **2444** icons.

- [FontAwesome 4.4](http://fortawesome.github.io/Font-Awesome/) Contains **585** icons
- [ionicons 2.0.0](http://ionicons.com/) Contains **733** icons, lots of iOS 7 style outlined icons.
- [Foundation icons](http://zurb.com/playground/foundation-icon-fonts-3) Contains **283** icons.
- [Zocial](http://zocial.smcllns.com/) Contains **99** social icons.
- [Material design icons ](https://github.com/google/material-design-icons) Contains **744** social icons.

An icon has a name, size, and a color (optional)

## Getting started

1. `npm install react-native-icons@latest --save`
2. In XCode, in the project navigator right click `Libraries` ➜ `Add Files to [your project's name]`
3. Go to `node_modules` ➜ `react-native-icons`➜ `ios` and add `ReactNativeIcons.xcodeproj` 
4. Add `libReactNativeIcons.a` (from 'Products' under ReactNativeIcons.xcodeproj) to your project's `Build Phases` ➜ `Link Binary With Libraries` phase
5. Add the font files you want to use into the `Copy Bundle Resources` build phase of your project (click the '+' and click 'Add Other...' then choose the font files from  `node_modules/react-native-icons/ios/ReactNativeIcons/Libraries/FontAwesomeKit`).
6. Run your project (`Cmd+R`)

## Notes

- You only need to include the icon font files you want to use 
- Icon style must set a width and height, or the icon will not be visible
- You may need to restart your node server for the icon font files to be included.

## Example of icons

```js
var { Icon, } = require('react-native-icons');


<Icon
  name='ion|beer'
  size={150}
  color='#887700'
  style={styles.beer}
/>
<Icon
  name='zocial|github'
  size={70}
  color='black'
  style={styles.github}
/>
<Icon
  name='fontawesome|facebook-square'
  size={70}
  color='#3b5998'
  style={styles.facebook}
/>
<Icon
  name='foundation|lightbulb'
  size={30}
  color='#777777'
  style={styles.lightbulb}
/>

<Icon
  name='material|face'
  size={30}
  color='#333333'
  style={styles.face}
/>

```

## Stacked icons

```js
<Icon
  name='fontawesome|square'
  size={80}
  color='#55acee'
  style={styles.twitterOutline}>
  <Icon
    name='fontawesome|twitter'
    size={50}
    color='#ffffff'
    style={styles.twitterIcon}/>
</Icon>
```

With the following styles to center them:

```js
var styles = StyleSheet.create({
  twitterOutline: {
    flexDirection: 'column',
    width: 70,
    height: 70,
    alignItems: 'center'
  },
  twitterIcon: {
    flex: 1,
    width: 40,
    height: 40
  },
});
```

## Custom tab bar

```js

var { TabBarIOS, } = require('react-native-icons');
var TabBarItemIOS = TabBarIOS.Item;

var Example = React.createClass({
  getInitialState: function() {
    return {
      selectedTab: 'home',
      notifCount: 0,
      presses: 0,
    };
  },
  render: function () {
    return (
      <TabBarIOS
        selectedTab={this.state.selectedTab}
        tintColor={'#c1d82f'}
        barTintColor={'#000000'}
        styles={styles.tabBar}>
        <TabBarItemIOS
          name="home"
          iconName={'ion|ios-home-outline'}
          selectedIconName={'ion|ios-home'}
          title={''}
          iconSize={32}
          accessibilityLabel="Home Tab"
          selected={this.state.selectedTab === 'home'}
          onPress={() => {
            this.setState({
              selectedTab: 'home',
            });
          }}>
          {this._renderContent()}
        </TabBarItemIOS>
        <TabBarItemIOS
            name="articles"
            iconName={'ion|ios-paper-outline'}
            selectedIconName={'ion|ios-paper'}
            title={''}
            iconSize={32}
            accessibilityLabel="Articles Tab"
            selected={this.state.selectedTab === 'articles'}
            onPress={() => {
            this.setState({
              selectedTab: 'articles',
            });
          }}>
          {this._renderContent()}
        </TabBarItemIOS>
        <TabBarItemIOS
            name="messages"
            iconName={'ion|chatboxes'}
            title={''}
            iconSize={32}
            accessibilityLabel="Messages Tab"
            selected={this.state.selectedTab === 'messages'}
            onPress={() => {
            this.setState({
              selectedTab: 'messages',
            });
          }}>
          {this._renderContent()}
        </TabBarItemIOS>
        <TabBarItemIOS
            name="settings"
            iconName={'ion|ios-gear-outline'}
            selectedIconName={'ion|ios-gear'}
            title={''}
            iconSize={32}
            accessibilityLabel="Settings Tab"
            selected={this.state.selectedTab === 'settings'}
            onPress={() => {
            this.setState({
              selectedTab: 'settings',
            });
          }}>
          {this._renderContent()}
        </TabBarItemIOS>
      </TabBarIOS>
    );
  }
});
```

**Note:** `selectedIconName` is optional. It defaults to `iconName` if not set. Also, there's another optional property named `selectedIconSize`, if you need to change the icon size when the tab is selected.


![Screenshot](https://dl.dropboxusercontent.com/u/6721696/stacked-demo.png)
