## [64-3 Create simple Top Banner react responsive carousel](https://web.programming-hero.com/web-9/video/web-9-64-3-create-simple-top-banner-react-responsive-carousel)
## [awesome-react-components](https://github.com/brillout/awesome-react-components)

#### [React Responsive Carousel](https://react-responsive-carousel.js.org/)
# project: msr-restaurant
```jsx
import "react-responsive-carousel/lib/styles/carousel.min.css"; // requires a loader
import { Carousel } from 'react-responsive-carousel';
import img1 from "../../assets/home/01.jpg"
import img2 from "../../assets/home/02.jpg"
import img3 from "../../assets/home/03.png"
import img4 from "../../assets/home/04.jpg"
import img5 from "../../assets/home/05.png"
import img6 from "../../assets/home/06.png"
const Banner = () => {
    return (
        <div>
             <Carousel>
                <div>                    <img src={img1} />
                </div>
                <div>
                    <img src={img2} />
                </div>
                <div>
                    <img src={img3} />
                </div>
                <div>
                    <img src={img4} />
                </div>
                <div>
                    <img src={img5} />
                </div>
                <div>
                    <img src={img6} />
                </div>
            </Carousel>
        </div>
    );
};

export default Banner;
```