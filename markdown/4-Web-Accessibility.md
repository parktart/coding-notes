# Web Accessibility

## Intro

Web accessibility refers to the inclusive practice of designing and developing websites that can be accessed and used by people with disabilities. It involves making websites perceivable, operable, understandable, and robust for all users, regardless of their abilities or disabilities.

**Inclusivity**: Web accessibility aims to ensure that everyone, including people with disabilities, can access and interact with websites. It emphasizes the removal of barriers that might prevent equal access and participation.

**Disability categories**: Web accessibility encompasses a wide range of disabilities,Web accessibility encompasses all disabilities that affect access to the Web, including auditory, cognitive, neurological, physical, speech and visual. Understanding the challenges faced by users with different disabilities will help you design more inclusive websites.

**Other categories**: Web accessibility also benefits people without disabilities, for example: on mobile phones, smart watches, smart TVs, and other devices with small screens, different input modes, older people, temporary disabilities such as a broken arm, situational limitations such as bright sunlight or an environment where you can't listen to audio, even slow internet connection or expensive bandwidth

**Standards and guidelines**: There are internationally recognized standards and guidelines that provide best practices for web accessibility. The Web Content Accessibility Guidelines (WCAG) is the most widely used and authoritative set of guidelines.



**Web Content Accessibility Guidelines (WCAG)**: WCAG is a set of guidelines developed by the World Wide Web Consortium (W3C) that provides a framework for creating accessible web content. It is organized into four principles: Perceivable, Operable, Understandable, and Robust (commonly referred to as the "POUR" principles). Each principle has specific guidelines and success criteria to help ensure accessibility.

1. **Perceivable**: Perceivability refers to ensuring that information on a website is available to all users. This involves providing text alternatives for non-text content, offering captions for multimedia, and designing for color-blind users.
2. **Operable**: Operability focuses on making websites functional and navigable for all users. It involves providing keyboard accessibility, giving users enough time to interact with content, and avoiding content that could cause seizures or physical reactions.
3. **Understandable**: Understandability ensures that website content and functionality are clear and easy to comprehend for all users. It includes using plain language, organizing content logically, and providing clear instructions.
4. **Robust**: Robustness refers to creating websites that can be interpreted and accessed by a wide variety of user agents (e.g., browsers, assistive technologies). It involves using standard HTML, CSS, and JavaScript practices to ensure compatibility and future-proofing.



In addition to WCAG, it's worth exploring other resources and standards like the Accessible Rich Internet Applications (ARIA) specification, which provides additional techniques for enhancing web accessibility, particularly for dynamic and interactive content.



## WCAG 2

The W3C Web Accessibility Initiative (WAI) develops technical specifications, guidelines, techniques, and supporting resources that describe accessibility solutions. These are considered international standards for web accessibility.

WCAG 2 is the current standard for Web Content Accessibility Guidelines

WCAG 2.0 is also an ISO standard: ISO/IEC 40500





## Examples

#### Alt text for images

Images should include alt text in the markup/code to make it accessible to use a screen reader as well as people who turn off images.



#### Keyboard Input

An accessible website does not rely on the mouse; it makes all functionality available from a keyboard. People with disabilities can then use assistive technologies that mimic the keyboard, such as speech input.



#### Audio Transcripts

Providing a text transcripts makes audio information accessible to people who are deaf or hard of hearing, as well as search engines and other technologies.



## Keyboard-navigable JavaScript widgets

Widgets are typically composed of `<div>` and `<span>` elements which do not, by nature, offer keyboard functionality

#### tabIndex

`tabindex` html attribute = `tabIndex` in JSX

By default, when people use the tab key to browse a webpage, only interactive elements (like links, form controls, buttons) get focused. Authors can add the `tabIndex` global attribute to other html elements to make them focusable too.

The order in which elements gain focus when using a keyboard is, by default, the html source order. Authors may want to redefine the order by setting `tabIndex` to any positive number.

`tabIndex = 0` element becomes focusable by keyboard and script

`tabIndex = -1` element becomes focusable by script (with `element.focus()`)

`tabIndex = 33` element becomes focusable by keyboard and script - tab order determined by number

NOTE elements with a positive tabIndex are put before the default interactive elements on the page, which means page authors will have to set (and maintain) tabIndex values for all focusable elements on the page when one or more positive tabIndex values are used.



#### Grouping controls

For grouping widgets such as menus, tablists, grids, or tree views, the parent element should be in the tab order (tabindex="0"), and each descendant choice/tab/cell/row should be removed from the tab order (tabindex="-1"). Users should be able to navigate the descendant elements using arrow keys.



## Accessibility in React



Although standard HTML practices can be directly used in React, note that the `for` attribute is written as `htmlFor` in JSX:

```jsx
<label htmlFor="inputX">Name:</label>
<input id="inputX" type="text" name="name"/>
```



#### Programmatically managing focus

React applications continuously modify the HTML DOM during runtime, which can lead to keyboard focus being lost or set to an unexpected element. In this case we can programmatically set the keyboard focus. 

To set focus in React, we can use Refs to DOM elements.

```jsx
import { useRef } from 'react';

export default function Form() {
  const inputRef = useRef(null);

  function handleClick() {
    inputRef.current.focus();
  }

  return (
    <>
      <input ref={inputRef} />
      <button onClick={handleClick}>
        Focus the input
      </button>
    </>
  );
}
```



By default React does not let a component access the DOM nodes of other components. Not even for its own children! This is intentional. Refs are an escape hatch that should be used sparingly. Manually manipulating *another* component's DOM nodes makes your code more fragile. However it can be done, for example, to reset keyboard focus to a button that opened a modal window after that modal window is closed.

```jsx
import { useRef } from "react";

export default function Container() {
    const buttonRef = useRef(null);

    return (
        <>
            <button ref={buttonRef} onClick={() => setWidgetOpen(true)}>
                Open Widge!
            </button>
            {widgetOpen && <Widget buttonRef={buttonRef} />}
        </>
    );
};

const Widget = ({ buttonRef }) => {
    return (
        <>
            <h1>This is a widget!</h1>
            <button
              	autoFocus
                onClick={() => {
                    setWidgetOpen(false);
                    buttonRef.current.focus(); // PROGRAMMATICALLY MANAGE FOCUS
                }}>
                Close
            </button>
        </>
    );
};
```

Here we gave accessed a *parent's* DOM element from a child. This is as simple as passing the ref down to the child, and using it there.

Note, by default, you cannot set a `ref` on a component directly..

```jsx
<MyInput ref={inputRef} /> // error
```

But if we do want to allow for this, we can use the `forwardRef` API

which also handles passing refs from child to parent elegantly..

```jsx
import { forwardRef, useRef } from 'react';

export default function Form() {
  const inputRef = useRef(null);

  return (
    <>
      <MyInput ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>
        Focus the input
      </button>
    </>
  );
}

const MyInput = forwardRef( (props, ref) => {
  return <input ref={ref} />;
});
```

Here we gave accessed a *child's* DOM element from a parent.

And we can even use `forwardRef` to pass a ref up through multiple components..

```jsx
export default function Form() {
  const ref = useRef(null);

  return (
    <form>
      <FormField label="Enter your name:" ref={ref} isRequired={true} />
      <button type="button" onClick={() =>  ref.current.focus()}>
        Edit
      </button>
    </form>
  );
}

const FormField = forwardRef((props, ref) => {
  // ...
  return (
    <>
      <MyInput ref={ref} />
      ...
    </>
  );
});

const MyInput = forwardRef((props, ref) => {
  return <input ref={ref} />;
});
```

