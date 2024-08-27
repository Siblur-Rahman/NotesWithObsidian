[46-4 Custom hook and create your first custom hook](https://web.programming-hero.com/web-9/video/web-9-46-4-custom-hook-and-create-your-first-custom-hook)
[61-6 Introduction to custom hooks](https://web.programming-hero.com/web-9/video/web-9-61-6-introduction-to-custom-hooks)

### #useAuth

```jsx
import { useContext } from "react";
import { AuthContext } from "../providers/AuthProvider";

const useAuth = () => {
    const auth = useContext(AuthContext);
    return auth;
};
export default useAuth;
```
### #Import UseAuth
```jsx
    const { signIn } = useAuth();
```
## useServics



```jsx
import { useEffect, useState } from "react";

const useServices = () => {
    const [services, setServices] = useState([]);
    
    useEffect(() => {
        fetch(`${import.meta.env.VITE_API_URL}/services`)
            .then(res => res.json())
            .then(data => setServices(data));
    }, [])
    return services
};
export default useServices;
```
## import
```jsx
    const services = useServices()
```