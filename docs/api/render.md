# Static Rendering API

Reagent's `render` function is used to render react components to static HTML and analyze the 
resulting HTML structure.

`render` returns a wrapper very similar to the other renderers in reagent, [`mount`](mount.md) and 
[`shallow`](shallow.md); however, `render` uses a third party HTML parsing and traversal library 
[Cheerio](http://cheeriojs.github.io/cheerio/). We believe that Cheerio handles parsing and 
traversing HTML extremely well, and duplicating this functionality ourselves would be a 
disservice.
 
For the purposes of this documentation, we will refer to Cheerio's constructor as 
`CheerioWrapper`, which is to say that it is analogous to our `ReactWrapper` and `ShallowWrapper`
constructors.

### Exmple Usage

```jsx
import { render } from 'reagent';

describe('<Foo />', () => {

  it('renders three `.foo-bar`s', () => {
    const wrapper = render(<Foo />);
    expect(wrapper.find('.foo-bar')).to.have.length(3);
  });

  it('rendered the title', () => {
    const wrapper = render(<Foo title="unique" />);
    expect(wrapper.text()).to.contain("unique");
  });

});
```
