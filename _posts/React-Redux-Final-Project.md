## Creating My Final Project and Connect()ing the Concepts 

For my final project here at Flatiron, I decided to make an app that will allow the user to keep a tracking on their financial situation. The idea behind this was that in the modern day where swiping a card is so easy it can sometimes become difficult to keep track of your money and keep from getting into serious trouble. Using the app I have built a user would be able to access a list of accounts they have and then add credits/debits to each account giving them a running amount of the balance in the account. They also can create accounts as needed. During this project build the the thing that made me struggle the most was the concept of `connect()` and by extension the `mapStateToProps` and `mapDispatchToProps`. These are concepts that to me felt like I understood them, but they were difficult for me to wrap my head around. Although I frequently feel that I am alone and even at times that I am downright dumb and learning any sort of coding is flatout a waste of time and lost cause for me I am going to act for a moment like that isn't the case and write this blog to help anyone that may be going through this same struggle with these concepts. 

# What is connect()? 

`Connect()` is a function provided to us via the `react-redux` that allows us to give a React component access to the app's store. Via this access to the store the connected component can get pieces of the store that it may need to either render data or dispatch actions back to the store to change/update it in some way. 

`Connect()` takes in up to 4 arguments, but the 2 most common are `mapStateToProps` and `mapDispatchToProps`, which we will talk about later in this blog. It uses these arguments to then listen for changes in the store and update the Props of the component accordingly. 

# How To Use connect()

When using `connect()` the first thing that must be done is making the store available to the app overall which is done is the index.js file by: 

```
import { Provider } from 'react-redux'
...

ReactDOM.render(
  <Provider store={store}>
    <AppName/>
  </Provider>
```

Once this has been done we can move into the component that we want to connect to the store and import the connect function in it then write the connect line at the bottom of the component. A usual component that uses connect() may be like this:

```
// componentName.js
import {connect} from 'react-redux'
... 

const mapStateToProps = (state) => {
  return {
    // some data from the state 
  }} 
  
 const mapDispatchToProps = {
  // object with action creators or function taking dispatch as an argument
 }
 
 export connect(mapStateToProps, mapDispatchToProps)(ComponentName)
```
This is now allowing the Component to access the data that is held in the apps Store. 

# Quick Rundown on mapStateToProps
 
 As mentioned above, one of the optional arguments, and one of the most frequently used ones is the `mapStateToProps`. This is a function that takes in the argument of `state`, which is the entire state of the store (as well as an optional second argument `ownProps`, which we will not focus on in this blog) and returns a POJO (Plain Old JavaScriptObject with the data in the store. An example of this is: 
 
 ```
 function mapStateToProps(state) {
  return {
    name: state.name,
    age: state.age
  }
 }
 ```
 or alternatively 
 ```
 const mapStateToProps = state => {
  return {
    name: state.name,
    age: state.age
  }
 }
 ```
 The `mapStateToProps` function is typically used to change the store data in some way such as returning only a specific value to be used as a prop in the component. 
 
#Quick Rundown of mapDispatchToProps

The other most frequently used argument for `connect()` is `mapDispatchToProps`. This is a function that allows you to create an action creator which are then passed to the component as props. This in turn makes it so that you can tell the component the exact actions it may need to dispatch and thus makes the dispahc more declaraive. 

There are 2 ways of using mapDispatchToProps, a function or an object. With it as a function you can customize it more and make it so the component calls more custom functions. An example of this is:

```
const mapDispatchToProps = (dispatch) => {
  return {
    // the actions you want dispatched such as:
    increase: () => dispatch({type: 'INCREASE_COUNT'})
    decrease: () => dispatch({type: 'DECREASE_COUNT'})
    ...
  }
 }
```

Using mapDispatchToProps as an Object allows you to be more declarative. This is the preferred method of declaring mapDispatchToProps unless there is a specific need for customized dispatching. This looks like this: 

```
const mapDispatchToProps = {
  increase,
  decrease,
}
```
