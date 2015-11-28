# material-tabs

## Get started

```
npm install --save material-tabs
```

## Example

![demo](https://i.gyazo.com/15c7deec2213018a1e6e6fc926bcb646.gif)

### Components

The package provides 2 components: Tab and TabGroup, used together like so:

``` js
import {Tab, TabGroup} from 'material-tabs';

const NavigationTabs = React.createClass({
  render: function() {
    return (
      <TabGroup>
        <Tab>
          One
        </Tab>
        <Tab>
          Two
        </Tab>
      </TabGroup>
    );
  }
)};
```

The following aspects are determined as a result of the number of children ```TabGroup``` has:

- The position of the indicator (underline), highlighting which tab was clicked and
- The width of each ```Tab```.

Meaning each Tab will always be identical in width.

#### TabGroup

By default, the following styles are applied:

- ```TabGroup``` is 100% width of it's parent,
- The indicator is #FFFFFF (white).
- Background colors are default (inherit).

```TabGroup``` accepts the following style prop:

```js
style={ indicator: { color: '#FF5722' } }
```

```TabGroup``` accepts an ```onChangeTab``` prop which passes the index of the newly selected ```Tab``` back up, used like so:

```js
render: function() {
  return (
    <TabGroup onChangeTab={this.handleChange}>
      <Tab>
        One
      </Tab>
      <Tab>
        Two
      </Tab>
    </TabGroup>
  );
},

handleChange: function(index) {
  console.log(index); // 1
}
```

It also accept a ```defaultSelectedTab``` prop which expects the index of the tab to be selected on initial render, which by default is of course ```0```. This is useful when persisting the currently selected tab across different routes.

Because the ```TabGroup``` component only cares about how many children it has (as opposed to what the children actually are), it's very easy to use the ```Tab```s as links (with, for example, the very excellent and highly recommended [React-router](https://github.com/rackt/react-router)). For example:

```js
render: function() {
  return (
    <TabGroup>
      <Link to='home'>
        <Tab>
          Home
        </Tab>
      </Link>
      <Link to='favourites'>
        <Tab>
          Favourites
        </Tab>
      </Link>
    </TabGroup>
  );
}
```

will render exactly the same without links (save for default link styling).

#### Tab

By default, the following styles are applied:

- The currently selected ```Tab``` text color is #FFFFFF (white),
- Unselected ```Tab```s are the same color, with an opacity of 0.7 applied,
- Background colors are default (inherit).

All other styles follow the [spec](https://www.google.com/design/spec/components/tabs.html#tabs-specs), such as text styling, spacing, heights, and animation.

```Tab``` accepts the following style prop:

```js
style={ color: '#FF5722' }
```

```Tab``` accepts a regular ```onClick``` prop as you would expect.

### Todo
- Add support for [icons with text](https://www.google.com/design/spec/components/tabs.html#tabs-specs)
- Add touch animations
