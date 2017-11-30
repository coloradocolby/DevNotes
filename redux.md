

# Redux
Redux serves to construct the application state while React provides the views to display those states. The two libraries are independent of each other

*What is react-redux*

React-Redux is a separate library that bridges the gap between the two.

#### Reducer
A reducer is a function that returns a piece of the application state. We can have many reducers.

```
export default function(state = null, action) {
  switch(action.type) {
    case 'BOOK_SELECTED':
     return action.payload;
  }
  return state
}
```

The reducers get tied together inside the combineReducers method:

```
const rootReducer = combineReducers({
  books: BooksReducer,
  activeBook: ActiveBook
});
```

#### Container
Container is a normal react component that gets bonded to the application state. When the application state changes the container will re-render

dispatch is a prop available on connected components

```
import React, { Component } from 'react';
import { connect } from 'react-redux';
import { selectBook } from '../actions/index';
import { bindActionCreators } from 'redux';

class BookList extends Component {

  renderList() {
    return this.props.books.map( book => {
      return (
        <li
          key={book.title}
          className="list-group-item"
          onClick={() => this.props.selectBook(book)}>
          {book.title}
        </li>
      )
    })
  }

  render() {
    return (
      <ul className="list-group col-sm-4">
        {this.renderList()}
      </ul>
    )
  }
}

function mapStateToProps(state) {
    // whatever is returned will show up as props inside of BookList
    return {
      books: state.books
    };
}

// anything returned from this function will end up as props on the BookList container
function mapDispatchToProps(dispatch) {
  // whenever selectBook is called, the result should be passed to all of our reducers
  // dispatch takes all of the actions, receives them, and then sends them to all reducers
  return bindActionCreators({ selectBook: selectBook }, dispatch)
}

// promote BookList from a component to a container -- it needs to know about this
// new dispatch method, selectBook. Make it available as a prop
export default connect(mapStateToProps, mapDispatchToProps)(BookList);

```
*Which components should we promote to a container?*

The most parent component that cares about a particular piece of state should be the container.



#### Action Creator
A function that returns an action

  1)  component calls action generator
  2)  action generator returns object
  3)  component dispatches object
  4)  redux store changes

  1)  component calls action generator
  2)  action generator returns function
  3)  component dispatches function (?)
  4)  function runs (has the ability to 
      dispatch other actions and do whatever it wants)
      
```
export function selectBook(book) {
  // selectBook is an ActionCreator, it needs to return an action an object with a type property
  return {
    type: 'BOOK_SELECTED',
    payload: book
  }
}

```
#### Action
An object that flows through all of our reducers. A reducer can then decide if it wants to change it's state based on the action.



Actions must always have a type defined, and they may optionally have something like payload defined:

```
return {
  type: 'BOOK_SELECTED',
  payload: book
}
```

#### Middleware
Middlewares are functions that take an action, and depending on the action's type and payload, or any other number of factors, the middleware can choose to let the action pass through, manipulate it, console log it, or stop it altogether, *before they reach a reducer.* Think of them like a gatekeeper, bouncer, or doorman. They stop any action, inspect it, and decide what to do.

#### Application state is entirely different than components state
Even with redux, a component still has access to it's personal state through this.state.xxx or this.setState({})

#### Store
You can subscribe to the store to be notified everytime it changes
```
store.subscribe(() => {
  const state = store.getState();
  const visibleExpenses = getVisibleExpenses(state.expenses, state.filters);
  console.log(visibleExpenses);
});
```

#### HOC

  const ConnectedExpenseList = connect((state) => {
    return {
      expenses: state.expenses
    };
  })(ExpenseList);

                                  1.        2.          3. 
  const ConnectedExpenseList = connect( (state) => )(ExpenseList);

  1.  We get something back from this is not the HOC
      it is the function. So we need to call that
  2.  What information from the store we want our
      component to be able to access
  3.  We call that with ExpenseList- which is what we 
      want to connect


const ConnectedExpenseList = connect((state) => ({ expenses: state.expenses}))(ExpenseList);


export default connect((state) => ({ expenses: state.expenses}))(ExpenseList);

const mapStateToProps = (state) => {
  return {
    expenses: state.expenses
  };
};

export default connect(mapStateToProps)(ExpenseList);

