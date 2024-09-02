## [63_5-3 Indexing and text search in mongodb](https://web.programming-hero.com/web-9/video/web-9-63_5-3-indexing-and-text-search-in-mongodb)
### [Case-Insensitive Queries Without Case-Insensitive Indexes](https://www.mongodb.com/developer/products/mongodb/schema-design-anti-pattern-case-insensitive-query-index/)


## <span style="color: red">Client Side</span>
```jsx
import { useState } from "react";
import useServices from "../../../hooks/useServices";
import ServiceCard from "./ServiceCard";
  
  

const Services = () => {
    const [asc, setAsc] = useState(true)
    const [search, setSearch] = useState('')
    const services = useServices(asc, search)
const handleSearch = (e) =>{
 e.preventDefault();
 const searchText = e.target.search.value;
 setSearch(searchText)
}
    return (
        <div className="mt-4">

           <div className="text-center">
                <h3 className="text-2xl font-bold text-orange-600">Our Services</h3>
                <h2 className="text-5xl">Our Service Area</h2>
                <p>the majority have suffered alteration in some form, by injected humour, or randomised <br /> words which do not look even slightly believable. </p>
                <form onSubmit={handleSearch}>
                <input type="text" name="search" id="" />
                <input type="submit" value="Search"  className="btn"/>
                </form>
                <button
                className="btn btn-secondary"
                onClick={() => setAsc(!asc)}
                >
                    {asc ? 'Price: High To Low' : 'Price Low To High'}
                </button>
            </div>
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                {
                    services.map(service => <ServiceCard
                        key={service._id}
                        service={service}
                    ></ServiceCard>)
                }
            </div>
        </div>
    );
};
  
export default Services;
```
## <span style="color: red">useServices</span>
```jsx
import { useEffect, useState } from "react";
import { axiosSecure } from "./useAxiosSecure";
const useServices = (asc, search) => {
   const [services, setServices] = useState([]);
    useEffect(() => {
        // fetch(`${import.meta.env.VITE_API_URL}/services`)
        //     .then(res => res.json())
        //     .then(data => setServices(data));
        axiosSecure(`/services?sort=${asc? 'asc' : 'desc'}&search=${search}`)
        .then(res => setServices(res.data))
    }, [asc, search])

    return services

};

export default useServices;
```
## <span style="color: red">ServiceCard</span>
```jsx
import { Link } from "react-router-dom";

const ServiceCard = ({ service }) => {
    const { _id, title, img, price } = service;
    return (

        <div className="card w-96 bg-base-100 shadow-xl">
            <figure className="px-10 pt-10">
                <img src={img} alt="Shoes" className="rounded-xl" />
            </figure>
            <div className="card-body">
                <h2 className="card-title">{title}</h2>
                <p className="text-xl text-orange-500">Price: ${price}</p>
                <div className="card-actions">
                    <Link to={`/book/${_id}`}>
                        <button className="btn btn-primary">Book Now</button>
                    </Link>
                </div>
            </div>
        </div>
    );
};
export default ServiceCard;
```
  
## <span style="color: red">Server</span>
```js

      app.get('/services', async (req, res) => {

        const filter = req.query;

        // const query = {
          // price: {$ne: 150, $gt: 20}
          // price: {$ne: 150}
          // price: {$gte: 150}
          // price: {$gt: 150}
          // price: {$lt: 150}
        // };
        const query = {
          title: {$regex: filter.search, $options: 'i'}
        }
        console.log(filter.search)
        const options = {
          sort: {
            price: filter.sort === 'asc' ? 1: -1
          }
        }
          const cursor = serviceCollection.find(query, options);
          const result = await cursor.toArray();
          res.send(result);
      })
```



