# vue-tabs-chrome
A Vue component for Chrome-like tabs.<br>
Drag-and-drop support provided by Draggabilly by @desandro.

## Live Demo
[https://viewweiwu.github.io/vue-tabs-chrome/](https://viewweiwu.github.io/vue-tabs-chrome/)

## Install
```
npm install --save vue-tabs-chrome
```

## Usage
``` html
<template>
  <vue-tabs-chrome v-model="tab" :tabs="tabs" />
</template>
<script>
export default {
  data () {
    return {
      tab: 'google',
      tabs: [
        {
          label: 'google',
          key: 'google',
          closable: false,
          favico: require('./assets/google.jpg')
        },
        {
          label: 'facebook',
          key: 'facebook',
          favico: require('./assets/fb.jpg')
        },
        {
          label: 'New Tab',
          key: 'costom key',
          favico: (h, { tab, index }) => {
            return h('span', tab.label)
          }
        }
      ]
    }
  }
}
</script>
```

## Attributes

| Attributes | Description | Type | Default |
| - | - | - | - |
| tabs | tabs configuration. Details are mentioned below. | Array | [] |
| value / v-model | binding value | String | - |
| props | configuration options, Details are mentioned below. |
| insert-to-after | Insert to tag's after | Boolean | false |
| is-mousedown-active | set tab is active when mousedown | Boolean | true |
| renderLabel | render label | Function(tab, index) | - |

## Tabs Attributes
| Attributes | Description | Type | Default |
| - | - | - | - |
| label | tab label | String | - |
| key | tab key | String | - |
| closable | tab closable | Boolean | true |
| favico | tab favico. Custom favico renderer. It uses Vue's render function. It accepts two arguments: the first is h, the second is an object. including tab and index | Function, required image | - |

## Props Attributes
| Attributes | Description | Type | Default |
| - | - | - | - |
| label | specify which key of tab object is used as the tab's label | String | 'label' |
| key | specify which key of tab object is used as the tab's key | String | 'key' |

## Methods 
| Method | Description | Parameters |
| - | - | - |
| addTab | add tab | (tab1, [, ...tab, ...tabN]) |
| removeTab | remove tab | (tabKey or index) |
| getTabs | get tabs | - |

## Events
| Event Name | Description | Parameters |
| - | - | - |
| click | Triggered when the user's pointer is pressed and unpressed and has not moved enough to start dragging. | (event, tab, index) |
| swap | Swap tab | (tab, targetTab) |
| remove | Remove tab | (tab, index) |
| contextmenu | Contextmenu event | (event, tab, index) |

## License
MIT
