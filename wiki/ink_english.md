<!--
Meta Description: # Ink: A Comprehensive Guide to JavaScript's CSS-in-JS Solution ## Synopsis Ink is a powerful CSS-in-JS library for React applications that allows dev...
Meta Keywords: ink, styles, styled, const, theme
-->

# Ink: A Comprehensive Guide to JavaScript's CSS-in-JS Solution

## Synopsis
Ink is a powerful CSS-in-JS library for React applications that allows developers to style components using JavaScript. It enables dynamic styling and theming while maintaining the benefits of scoped styles.

## Documentation

### Purpose
Ink is designed to simplify the process of styling React components by allowing developers to write CSS directly within their JavaScript code. This approach not only enhances readability but also promotes maintainability and reusability of styles by encapsulating them within components.

### Usage
To use Ink in your project, follow these steps:

1. **Installation**: Install Ink via npm or yarn:
   ```bash
   npm install ink
   ```
   or
   ```bash
   yarn add ink
   ```

2. **Creating Styled Components**: Use the `styled` API provided by Ink to create styled components. Here is a basic example:
   ```javascript
   import { styled } from 'ink';

   const StyledText = styled.Text`
       color: blue;
       font-weight: bold;
   `;

   const MyComponent = () => (
       <StyledText>Hello, Ink!</StyledText>
   );
   ```

3. **Theming**: Ink supports theming, allowing you to define global styles and variables that can be accessed throughout your application:
   ```javascript
   import { ThemeProvider, styled } from 'ink';

   const theme = {
       primaryColor: 'blue',
       secondaryColor: 'green',
   };

   const ThemedText = styled.Text`
       color: ${props => props.theme.primaryColor};
   `;

   const App = () => (
       <ThemeProvider theme={theme}>
           <ThemedText>Hello, themed Ink!</ThemedText>
       </ThemeProvider>
   );
   ```

### Details
- **Scoped Styles**: Styles defined using Ink are scoped to the component, preventing style conflicts and making it easier to manage styles in large applications.
- **Dynamic Styling**: Ink allows for dynamic styling based on props, enabling you to create responsive and interactive designs effortlessly.
- **Server-Side Rendering**: Ink is compatible with server-side rendering (SSR), ensuring that your styles are properly rendered on both client and server.

## Examples

### Basic Example
```javascript
import { render } from 'ink';
import { styled } from 'ink';

const StyledText = styled.Text`
    color: green;
`;

const App = () => <StyledText>Hello, Ink!</StyledText>;

render(<App />);
```

### Theming Example
```javascript
import { render } from 'ink';
import { ThemeProvider, styled } from 'ink';

const theme = {
    primaryColor: 'purple',
};

const ThemedText = styled.Text`
    color: ${props => props.theme.primaryColor};
`;

const App = () => (
    <ThemeProvider theme={theme}>
        <ThemedText>Hello, themed Ink!</ThemedText>
    </ThemeProvider>
);

render(<App />);
```

## Explanation
- **Common Pitfalls**: One common mistake is forgetting to wrap your components in the `ThemeProvider` when using theming. Ensure that all styled components that rely on the theme are nested inside the provider.
- **Performance Considerations**: While Ink allows for powerful dynamic styling, overusing props for styles can lead to performance issues. It’s best to limit the use of dynamic styles to cases where they are truly necessary.
- **Static vs. Dynamic Styles**: Use static styles for consistent, unchanging styles, while dynamic styles should be reserved for cases where the style depends on component props or state.

## One Line Summary
Ink is a CSS-in-JS library for React that simplifies styling components by integrating styles directly within JavaScript, promoting maintainability and readability.