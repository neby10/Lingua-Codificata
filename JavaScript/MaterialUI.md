# Material UI

[Docs](https://mui.com/material-ui/getting-started/)


Typography Variants: h1 -> h6, subtitle1, subtitle2, body1, body2, button, caption, overline

Button Variants: text, contained, outlined

Custom Styling Example
~~~
import Button from '@mui/material/Button';
import { styled } from '@mui/material/styles;
const CustomButton = styled(Button) ({
    background: "purple",
    color: "white",
    '&:hover: {
        background: 'darkpurple',
    },
})
~~~