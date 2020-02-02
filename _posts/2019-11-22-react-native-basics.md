---
title: React Native Basics
---

By now, you should already have an environment for writing React Native from following [the previous React Native walkthrough](blog/{% post_url 2019-11-20-getting-started-with-react-native %}). Next, we will go over the basics. I will assume no knowledge of Javascript, React, or React Native.

## Javascript

Javascript is a popular programming language historically used for creating web applications that can be viewed in your browser. It operates on HTML, a markup language that specifies tags (including headers, lists, and images) that you see on a webpage and CSS, a language that specifies the style of tags in certain contexts. React is a framework for building web apps using Javascript. React and React Native use a similar markdown language to HTML called JSX, but the two are very similar with tags looking like ``<tag/>`` or ``<tag>text content</tag>``. 

Try going into your favorite web browser, right click, and select 'Inspect element' somewhere on the page. This will give you a feel of what HTML looks like. In Google Chrome, you can type ``Ctrl-Shift-i`` to enter the developers' tools. The 'Elements' tab will display the HTML as well as its associated CSS on the right hand side. Under 'Sources', you might find any Javascript files for the webpage.

Notice the attributes of the HTML elements. For example, ``<div id="sidebar"></div>``. These provide a mutable state for the elements that can be manipulated with Javascript and serve as conditions for styling with CSS.

You can learn more about Javascript [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript).

## React

React puts an emphasis on Javascript [classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) as well as some functional programming ideas like [constants](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const). The most important new features in React are the concepts of components, props, and state. 

Components are containers for the code of an element of a page's user interface. In React, they are a Javascript class that can be ``extend``ed.

```javascript
class Greeting extends React.Component {
	render() {
		return (
			<h1>Hello, {this.props.name}!</h1>
		);
	}
}
```

Notice that in the code above, I never specified what ``this.props.name`` should be or even its default value. This is because props are inherited by a parent component.

```javascript
class Letter extends React.Component {
	renderGreeting(name) {
		return <Greeting name={name} />;
	}
	...
}
```

Note that this allows data to be passed in a top-down approach. As a general rule, anything in the JSX enclosed by ``{}`` is Javascript. Props can also be used for specifying behavior, such as adding an ``onClick={function(){ alert("We got a 2319!"); }}`` attribute to a JSX element.

However once a prop is defined for a component, it cannot be changed. This is where state comes in as a solution for mutable data.

```javascript
class Birthday extends React.Component {
	constructor(props) {
		super(props);
		this.state = {
			age: 0,
		};
	}

	render() {
		return (
			<h2 onClick={function(){ this.setState({age: this.state.age+1}) }}>
				Yay, birthday #{this.state.age}!
			</h2>
		);
	}
}
```

For more info see [this guide](https://reactjs.org/tutorial/tutorial.html).

## React Native

React Native is framework that allows you to write Javascript code (which normally only runs on a web browser) to create mobile apps that run natively on Android or iOS.

React Native is obviously very similar to React. However, it has built-in components like ``<Text>``, ``<View``, ``<ScrollView>`` and more to create an interoperable framework for mobile app development.

For more info see [Facebook's (the creator of React Native) guide](https://facebook.github.io/react-native/docs/getting-started).
