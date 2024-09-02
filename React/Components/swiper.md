## [swiper](https://swiperjs.com/get-started)

## [64-4 Use swiper JS to create a category Swiper](https://web.programming-hero.com/web-9/video/web-9-64-4-use-swiper-js-to-create-a-category-swiper)

## <span style="color: red">msrRestaurant Home/Category/Category.jsx</span>
```jsx
// Import Swiper React components

import { Swiper, SwiperSlide } from 'swiper/react';

// Import Swiper styles

import 'swiper/css';

import 'swiper/css/pagination';

// import required modules
import { Pagination } from 'swiper/modules';
import slide1 from "../../../assets/home/slide1.jpg"
import slide2 from "../../../assets/home/slide2.jpg"
import slide3 from "../../../assets/home/slide3.jpg"
import slide4 from "../../../assets/home/slide4.jpg"
import slide5 from "../../../assets/home/slide5.jpg"
const Category = () => {
    return (
        <>
            <Swiper
        slidesPerView={4}
        spaceBetween={30}
        centeredSlides={true}
        pagination={{
          clickable: true,
        }}
        modules={[Pagination]}
        className="mySwiper mb-24"
      >
        <SwiperSlide>
            <img src={slide1}/>
            <h3 className='text-4xl uppercase text-center -mt-16 text-white'>Salad</h3>
        </SwiperSlide>
        <SwiperSlide>
            <img src={slide2}/>
            <h3 className='text-4xl uppercase text-center -mt-16 text-white'>soups</h3>
        </SwiperSlide>
        <SwiperSlide>
            <img src={slide3}/>
            <h3 className='text-4xl uppercase text-center -mt-16 text-white'>pizzas</h3>
        </SwiperSlide>
        <SwiperSlide>
            <img src={slide4}/>
            <h3 className='text-4xl uppercase text-center -mt-16 text-white'>dessserts</h3>
        </SwiperSlide>
        <SwiperSlide>
            <img src={slide5}/>
            <h3 className='text-4xl uppercase text-center -mt-16 text-white'>Salad</h3>
        </SwiperSlide>
      </Swiper>
        </>
    );
};
export default Category;
```

