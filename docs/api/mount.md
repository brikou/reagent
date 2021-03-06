# Full Rendering API (`mount(...)`)

Full DOM rendering is ideal for use cases where you have components that may interact with DOM apis,
or may require the full lifecycle in order to fully test the component (ie, `componentDidMount` 
etc.)

Full DOM rendering  depends on a library called [jsdom](https://github.com/tmpvar/jsdom) which is
essentially a headless browser implemented completely in JS.

```jsx
import { mount } from 'reagent';

describe('<Foo />', () => {

  it('calls componentDidMount', () => {
    spy(Foo.prototype, 'componentDidMount');
    const wrapper = mount(<Foo />);
    expect(Foo.prototype.componentDidMount.calledOnce).to.be.true;
  });

  it('allows us to set props', () => {
    const wrapper = mount(<Foo bar="baz" />);
    expect(wrapper.props().bar).to.equal("baz");
    wrapper.setProps({ bar: "foo" });
    expect(wrapper.props().bar).to.equal("foo");
  });

  it('simulates click events', () => {
    const onButtonClick = spy();
    const wrapper = mount(
      <Foo onButtonClick={onButtonClick} />
    );
    wrapper.find('button').click();
    expect(onButtonClick.calledOnce).to.be.true;
  });

});
```


## ReactWrapper API

#### [`.find(selector) => ReactWrapper`](ReactWrapper/find.md)
Find every node in the render tree that matches the provided selector.

#### [`.findWhere(predicate) => ReactWrapper`](ReactWrapper/findWhere.md)
Find every node in the render tree that return true for the provided predicate function.

#### [`.filter(selector) => ReactWrapper`](ReactWrapper/filter.md)
Remove nodes in the current wrapper that do not match the provided selector.

#### [`.filterWhere(predicate) => ReactWrapper`](ReactWrapper/filterWhere.md)
Remove nodes in the current wrapper that do not return true for the provided predicate function.

#### [`.contains(node) => Boolean`](ReactWrapper/contains.md) 
Returns whether or not a given node is somewhere in the render tree.

#### [`.hasClass(className) => Boolean`](ReactWrapper/hasClass.md)
Returns whether or not the current root node has the given class name or not.

#### [`.is(selector) => Boolean`](ReactWrapper/is.md)
Returns whether or not the current node matches a provided selector.

#### [`.not(selector) => ReactWrapper`](ReactWrapper/not.md)
Remove nodes in the current wrapper that match the provided selector. (inverse of `.filter()`)

#### [`.children() => ReactWrapper`](ReactWrapper/children.md)
Get a wrapper with all of the children nodes of the current wrapper.

#### [`.parents() => ReactWrapper`](ReactWrapper/parents.md)
Get a wrapper with all of the parents (ancestors) of the current node.

#### [`.parent() => ReactWrapper`](ReactWrapper/parent.md)
Get a wrapper with the direct parent of the current node.

#### [`.closest(selector) => ReactWrapper`](ReactWrapper/closest.md)
Get a wrapper with the first ancestor of the current node to match the provided selector.

#### [`.text() => String`](ReactWrapper/text.md)
Returns a string representation of the text nodes in the current render tree.

#### [`.get(index) => ReactWrapper`](ReactWrapper/get.md)
Returns the node at the provided index of the current wrapper.

#### [`.at(index) => ReactWrapper`](ReactWrapper/at.md)
Returns a wrapper of the node at the provided index of the current wrapper.

#### [`.first() => ReactWrapper`](ReactWrapper/first.md)
Returns a wrapper of the first node of the current wrapper.

#### [`.last() => ReactWrapper`](ReactWrapper/last.md)
Returns a wrapper of the last node of the current wrapper.

#### [`.state([key]) => Any`](ReactWrapper/state.md)
Returns the state of the root component.

#### [`.props() => Object`](ReactWrapper/props.md)
Returns the props of the root component.

#### [`.prop(key) => Any`](ReactWrapper/prop.md)
Returns the named prop of the root component.

#### [`.simulate(event[, data]) => ReactWrapper`](ReactWrapper/simulate.md)
Simulates an event on the current node.

#### [`.setState(nextState) => ReactWrapper`](ReactWrapper/setState.md)
Manually sets state of the root component.

#### [`.setProps(nextProps) => ReactWrapper`](ReactWrapper/setProps.md)
Manually sets props of the root component.

#### [`.instance() => ReactComponent`](ReactWrapper/instance.md)
Returns the instance of the root component.

#### [`.update() => ReactWrapper`](ReactWrapper/update.md)
Calls `.forceUpdate()` on the root component instance.

#### [`.type() => String|Function`](ReactWrapper/type.md)
Returns the type of the current node of the wrapper.

#### [`.forEach(fn) => ReactWrapper`](ReactWrapper/forEach.md)
Iterates through each node of the current wrapper and executes the provided function

#### [`.map(fn) => Array`](ReactWrapper/map.md)
Maps the current array of nodes to another array.

#### [`reduce(fn[, initialValue]) => Any`](/docs/api/ReactWrapper/reduce.md)
Reduces the current array of nodes to a value
 
#### [`reduceRight(fn[, initialValue]) => Any`](/docs/api/ReactWrapper/reduceRight.md)
Reduces the current array of nodes to a value, from right to left.
 
#### [`some(selector) => Boolean`](/docs/api/ReactWrapper/some.md)
Returns whether or not any of the nodes in the wrapper match the provided selector.

#### [`someWhere(predicate) => Boolean`](/docs/api/ReactWrapper/someWHere.md)
Returns whether or not any of the nodes in the wrapper pass the provided predicate function.

#### [`every(selector) => Boolean`](/docs/api/ReactWrapper/every.md)
Returns whether or not all of the nodes in the wrapper match the provided selector.

#### [`everyWhere(selector) => Boolean`](/docs/api/ReactWrapper/everyWhere.md)
Returns whether or not any of the nodes in the wrapper pass the provided predicate function.
