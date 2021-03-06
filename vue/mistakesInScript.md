## Script

#### Use single quotes and backticks instead of double quotes

###### Bad:
```javascript
  foo: "",
  bar: slug + "/files"
```
###### Good:
```javascript
  foo: '',
  bar: `${slug}/files`
```
<br><br>


#### Follow imports order

###### Bad:
```javascript
import { mapActions, mapGetters } from 'vuex'
import { required } from 'vuelidate/lib/validators'
import lodash from 'lodash'
import NewFormInterpritation from './NewFormInterpritation'
import preparePayload from '@/utils/preparePayload'
import { merge, path, pathOr, isEmpty } from 'ramda'
```
###### Good:
```javascript
// Vuex
import { mapActions, mapGetters } from 'vuex'

// Components
import NewFormInterpritation from './NewFormInterpritation'
import CustormFormField from './NewCustormFormField'

// Libs, utils, modules
import { required } from 'vuelidate/lib/validators'
import { merge, path, pathOr, isEmpty } from 'ramda'
import preparePayload from '@/utils/preparePayload'
import lodash from 'lodash'
```
<br><br>


#### Follow component [options order](https://vuejs.org/v2/style-guide/#Component-instance-options-order-recommended)

###### Bad:
```javascript
components
name
data
methods
mounted
created
props
computed
// ...
```
###### Good:
```javascript
name
components
mixins
props
data
computed
watch
methods
lifecycle methods in order they are called
```
<br><br>


#### Split actions and getters into multiple lines while mapping

###### Bad:
```javascript
...mapGetters(['agendaSettings', 'locationsList', 'sessionsList', 'totalSessionsPages', 'totalSessionsItems'])
```
###### Good:
```javascript
...mapGetters([
  'agendaSettings',
  'locationsList',
  'sessionsList',
  'totalSessionsPages',
  'totalSessionsItems'
])
```
<br><br>


#### Don't forget to stop listening for eventBus event in beforeDestroy

###### Bad:
```javascript
created () {
  // start listening
  this.$bus.$on('modalChangeVisibility', ...)
}
```
###### Good:
```javascript
created () {
  // start listening
  this.$bus.$on('modalChangeVisibility', ...)
},
beforeDestroy () {
  // stop listening (don't pass callback in $off)
  this.$bus.$off('modalChangeVisibility')
}
```
<br><br>


## Vuex

#### Mostly start mutation name from `SET`

###### Bad:
```javascript
[types.GET_FOO]
[types.NAME_FOO]
[types.FOO]
```
###### Good:
```javascript
[types.SET_FOO]
[types.UPDATE_FOO]
[types.ADD_TO_FOO]
```
<br><br>


#### Mostly start action name from `fetch`, `post`, `update`, `delete`

###### Bad:
```javascript
getItems
itemDelete
```
###### Good:
```javascript
fetchItems
updateItem
deleteItem
```
<br><br>
