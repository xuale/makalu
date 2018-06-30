# makalu

a reactive, declarative menu component :mount_fuji:

## Table of Contents
  - [Installation](#installation)
  - [Sample Code](#sample-code)
  - [Why makalu?](#why-makalu)
  - [API](#api)
    - [Menu](#menu)
    - [MenuSection](#menusection)
    - [MenuItem](#menuitem)

## Installation
## Sample Code

```html
<Menu
  horizontal
  isOpen={isMenuOpen}
  onMenuClose={this.closeMenu}
  position={{ top: "32px" }}
>
  <MenuSection title="first section">
    <MenuItem title="Create New Group" isSubmenu>
      <Menu horizontal submenu>
        <MenuSection title="first submenu">
          <MenuItem title="This Not A Submenu" />
          <MenuItem title="This Is In A Submenu" isSubmenu>
            <Menu horizontal submenu>
              <MenuSection title="second submenu">
                <MenuItem title="This Is In Submenu Two" to="/login" />
              </MenuSection>
            </Menu>
          </MenuItem>
        </MenuSection>
      </Menu>
    </MenuItem>
    <MenuItem title="This Is Disabled" disabled />
  </MenuSection>
  <MenuSection title="create a new thing">
    <MenuItem title="This Has An Icon" icon={<UserSettingsIcon />} />
    <MenuItem title="A Submenu Too" icon={<LockIcon />} isSubmenu>
      <Menu horizontal submenu>
        <MenuSection title="first section" />
      </Menu>
    </MenuItem>
  </MenuSection>
  <MenuSection
    title="search by title"
    isSearch
    searchSettings="Search for a name"
  >
    <MenuItem title="Search For Me" key="a" icon={<PlusIcon />} disabled />
    <MenuItem title="Search For Me" key="b" icon={<PlusIcon />} />
  </MenuSection>
</Menu>
```
## Why makalu?
makalu uses only three components to generate dynamic and nested dropdown menus: `Menu`, `MenuSection`, and `Menu`.  
  
It then wraps these components in an intuitive and hassle-free syntax, with individual items that can handle any functionality. :helicopter:  
  
The source code uses a modern stack, including [emotion](https://emotion.sh/docs/introduction) for styling.
## API
### `Menu`
The highest level wrapper, containing various `MenuSection` and `MenuItem` components. It is also used to nest submenus, further explained in [`MenuItem`](#menuitem).  
| Props |  Type  | Description |
| ------| ------ | ------------|
| horizontal | boolean | Determines alignment of menu |
| position | Object `{top: number, left: number}` | Determines absolute position of upper-left corner (only necessary for outermost `Menu`) |
| isOpen | boolean | `Menu` is visible only if true |
| onMenuClose | function | User-defined function for closing `Menu`, e.g. setting `isOpen` to false somehow|
### `MenuSection`
Partitions a `Menu` component into organizational sections and can contain `MenuItem` component(s). `MenuSection` also comes with a search feature to filter contained `MenuItem` components by their `key` prop.
| Props |  Type  | Description |
| ------| ------ | ------------|
| title | string | Determines section header |
| isSearch | boolean | Initializes current `MenuSection` to have a search filter if true |
| searchSettings | string | Determines placeholder text in the search bar, if `MenuSection` has `isSearch` equal to true |
### `MenuItem`
An individual item in a `Menu`. Generally, it displays a `title` and/or `icon`, but custom JSX can also be injected via the `render` prop. Upon being clicked, a `MenuItem` may either redirect to another route, generate a submenu, or perform a custom `onClick` function
| Props |  Type  | Description |
| ------| ------ | ------------|
| title | string | Determines main text |
| icon | JSX | Determines icon to be displayed alongside `title` |
| render | function | Can be used to render custom children inside the `MenuItem`. See [here](https://reactjs.org/docs/render-props.html) for more information |
| disabled | boolean | Makes `MenuItem` unclickable and visibly unavailable if true |
| isSubmenu | boolean | If true, `MenuItem` will render a child `Menu` component to its right when clicked (cannot be true with `to` and `onClick`)
| to | string | If defined, `MenuItem` will redirect to the given route when clicked (cannot be defined with `isSubmenu` and `onClick`) |
| onClick | function | If defined, `MenuItem` will perform the given function when clicked (cannot be defined with `isSubmenu` and `to`)|
| key | string| Must be used when nested inside a parent `MenuSection` with `isSearch` set to true. `key` determines the value by which the `MenuItem` can be searched by|  