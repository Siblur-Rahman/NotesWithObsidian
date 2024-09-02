## [React Helmet Async](https://www.npmjs.com/package/react-helmet-async)

[65-1 Dynamic Page Title By Route Using <span style="color: red">React Helmet</span> 9:35](https://web.programming-hero.com/web-9/video/web-9-65-1-dynamic-page-title-by-route-using-react-helmet)
## <span style="color: red">msr-Restaurant Menu file</span>
```jsx
import { Helmet } from "react-helmet-async";

const Menu = () => {
    return (
       <div>
        <Helmet>
            <title>Menu</title>
      </Helmet>
      <div>this is menu page</div>
        </div>
    );
};

  

export default Menu;
```
## <span style="color: red">main.jsx</span>
```jsx
import {HelmetProvider } from 'react-helmet-async';


createRoot(document.getElementById('root')).render(
  <StrictMode>
    <HelmetProvider>
      <div className='max-w-screen-xl mx-auto'>
        <RouterProvider router={router} />
      </div>
    </HelmetProvider>
  </StrictMode>,
)
```

