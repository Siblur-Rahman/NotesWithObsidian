## [65-2 Implement <span style="color: red">Cover</span>  With With <span style="color: red">Blur Parallax</span> Using React Parallax](https://web.programming-hero.com/web-9/video/web-9-65-2-implement-cover-with-with-blur-parallax-using-react-parallax)


## [65-2 Implement <span style="color: red">Cover</span> With With <span style="color: red">Blur Parallax</span>  Using React Parallax](https://web.programming-hero.com/web-9/video/web-9-65-2-implement-cover-with-with-blur-parallax-using-react-parallax)
## <span style="color: red">MSR Restaurant </span>shared/cover.jsx
```jsx
import { Parallax, Background } from 'react-parallax';  

const Cover = ({img, title}) => {
    return (
<Parallax
	blur={{ min: -50, max: 50 }}
	bgImage={img}
	bgImageAlt="the Menu"
	strength={-200}
>
	<div className="hero h-[700px]">
		<div className="hero-overlay bg-opacity-60"></div>
			<div className="hero-content text-neutral-content text-center">
			<div className="max-w-md">
			<h1 className="mb-5 text-5xl font-bold uppercase">{title}</h1>
			 <p className="mb-5"> {text} </p>
		   </div>
		</div>
	</div>
	
</Parallax>
);
};
export default Cover;
```


