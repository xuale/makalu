# makalu

a reactive, declarative menu component :mount_fuji:

## Table of Contents
  - [Installation](#installation)
  - [Sample Code](#sample-code)
  - [Why makalu?](#components-overview)
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
### Menu
### MenuSection
### MenuItem