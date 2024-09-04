[useNavigate](https://reactrouter.com/en/main/hooks/use-navigate)
## msrRestaurant Project: <span style="color: red">FoodCart.jsx</span>
```jsx
	import { useLocation, useNavigate } from 'react-router-dom';
	let location = useLocation();
	navigate("/login", { state: { from: location }});
```
<span style="color: red">Login.jsx</span>
```jsx
import {useLocation, useNavigate } from 'react-router-dom';
    const navigate = useNavigate();
    const location = useLocation()
    
    const from = location.state?.from?.pathname || "/";
    navigate(from, { replace: true });
```