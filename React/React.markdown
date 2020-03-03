## Why React
ReactJS makes a front-end system modular. So that system is easy to reuse, maintain and expand. It focus on the View layer
and it has functional component which is more appropriate for test.
### state&props
### React Element vs React Component
React element is a different concept to component. Actually, it is a return value of component.  
The form of element is object. And the type property determine which DOM element it will be convert to.
For them, the creation code is different. For element (DOM component) is React.creatElement. For component (composite 
component) is React.creatComponent.  
### stateless&stateful
### life cycle
#### Constructor
#### getDerivedStateFromProps
#### componentDidMount
#### shouldComponentUpdate
#### componentDidUpdate
#### getSnapshotBeforeUpdate
#### componentWillUnmount
### HOC
Aux; Error handler; Lazy loading
### Router
### Redux
用户状态，用户身份，是否登陆  
action creator, reducer  
props, dispatch  
## Hooks
结合functional component得出stateful component  
组件之间的复用状态逻辑很难  
复杂组件变得难以理解  
难以理解的class  
###对于stateful
useState + useReducer
### 对于逻辑整合
useEffect
### Redux
useSelector + useDispatch + useContext
### 对于shouldComponentUpdate
React.memo + useCallback



