# React Native Odometer

Odometer for React Native, supports numbers, localization and strings.

# Features

- Animations with `react-native-reanimated`.
- Custom animation duration via `duration` prop.
- Automatically measures all widths and heights of items and adjusts accordingly!
- Supply a `children` element with the number or string.
- Numbers can be formatted to custom locale via `locale` prop.
- Uses `tabular-nums` fontVariant to avoid layout shifting.

# Install

```
npm i react-native-odometer
```

If your React runtime does not support Intl but you want to use number localization, also install the polyfill or switch runtime.

```
npm i number-to-locale-string-polyfill
```

# Example

```jsx
import Odometer from "react-native-odometer";
```

## Simple Odometer

```jsx
<Odometer>12345.44</Odometer>
```

## Odometer with Localization

```jsx
<Odometer locale="en-IN">12345.44</Odometer>
```

## Custom Odometer

```jsx
const currencies = ["$", "₹", "€"];

const App = () => {
  const [state, setState] = useState({
      currency: currencies[0],
      value: 0
    });

  useEffect(() => {
    setInterval(() => {
      setState({
        currency: currencies[Math.floor(Math.random() * 3)],
        value: Math.floor(Math.random() * 1000000)
      });
    }, 500);
  }, []);

  return (
    <View>
      <Odometer>
        <Odometer.Fragment rotateItems={currencies}>{state.currency}</Odometer.Fragment>
        {state.value}
      </Odometer>
    </View>
  );
};
```
# Props

| Prop          	| Required 	| Default 	| Description                                                     	|
|---------------	|----------	|---------	|-----------------------------------------------------------------	|
| `children`    	| Yes      	| -       	| The Odometer number/text to render.                             	|
| `duration`    	| No       	| 500ms   	| Animation Duration                                              	|
| `textStyle`   	| No       	| -       	| Additional Styling for Text                                     	|
| `textProps`   	| No       	| -       	| Additional Props for Text                                       	|
| `rotateItems` 	| No       	| -       	| Only for Fragment. Possible characters for Odometer custom.     	|
| `locale`      	| No       	| ""      	| Localization identifier for numbers. Eg: "en-US", "en", "en-IN" 	|

## Thanks

React Native Odometer is based on `react-native-ticker`.