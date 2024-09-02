## [65-3 Create Custom Hook Usemenu To Load Menu Data <span style="color: red">5:00</span>](https://web.programming-hero.com/web-9/video/web-9-65-3-create-custom-hook-usemenu-to-load-menu-data)
<span style="color: red">MSR Restaurant</span> useMenu.jsx
```jsx
import { useEffect, useState } from "react";
const useMenu = () =>{
    const [menu, setMenu] = useState([]);
    const [loading, setLoading] = useState(true)
    useEffect(() =>{
        fetch('menu.json')
        .then(res =>res.json())
        .then(data => {
            setMenu(data)
            setLoading(false)
        })
    }, [])
return [menu, loading]
}
export default useMenu;
```
