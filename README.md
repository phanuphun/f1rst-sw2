## Installation
```shell
npm i f1rst-sw2
```
## Example
```ts
import MsgAlert from 'f1rst-sw2'

const _msg = new MsgAlert()

function toast(){
    _msg.toast_msg({ title: 'hello', icon: 'success' })
}

function lightBox(){
    _msg.lightBox('image_url','1200px')
}
```
