[Uses Example](https://www.mongodb.com/docs/drivers/node/current/usage-examples/#usage-examples)
[PH 67-2 4:40](https://web.programming-hero.com/web-9/video/web-9-67-2-enforce-user-to-login-before-add-to-the-cart)
## <span style="color: red">Client-side</span> project:  mrsRestaurant
```jsx
      fetch(`http://localhost:5000/carts`,{
        method:"POST",
        headers:{"Content-type":"application/json"},
        body:JSON.stringify(cartItem)
      })
      .then(res => res.json())
      .then(data =>{
        console.log(data)
      
        //we can show alert Here
        
    })
```
## <span style="color: red">Server-side </span> project:  mrsRestaurant
```jsx
     app.post("/carts", async(req, res) =>{
      const cartItem = req.body;
      const result = await cartsCollection.insertOne(cartItem);
      res.send(result)

     })
```


```jsx
  import React from 'react';
import useAuth from '../../hooks/useAuth';
import Swal from 'sweetalert2';
import axios from 'axios';
import { useLocation, useNavigate } from 'react-router-dom';

const FoodCard = ({item}) => {
  const {_id, name, image, price, recipe} = item;
  let location = useLocation();
  const navigate = useNavigate();
  const {user} = useAuth();
  const handleAddToCart = (food) =>{
    if(user && user.email){
      // ToDo: send cart item to the database
      const cartItem = {
        menuId: _id,
        email: user.email,
        name,
        image,
        price
      }
      fetch(`http://localhost:5000/carts`,{
        method:"POST",
        headers:{"Content-type":"application/json"},
        body:JSON.stringify(cartItem)
      })
      .then(res => res.json())

      .then(data =>{
        console.log(data)
        if(data?.insertedId){
          Swal.fire({
            position: "top-end",
            icon: "success",
            title: "Added Item to cart Successfully",
            showConfirmButton: false,
            timer: 1500
          });
        }
      })
    }else{
      Swal.fire({
        title: "You are not logged in",
        text: "Plese login to add to the Cart!",
        icon: "warning",
        showCancelButton: true,
        confirmButtonColor: "#3085d6",
        cancelButtonColor: "#d33",
        confirmButtonText: "Yes, Login!"
      }).then((result) => {
        if (result.isConfirmed) {
          // send the user to the login page
          navigate("/login", { state: { from: location }});
        }
      });
    }
    console.log(food, user.email)
  }
    return (
        <div>
            <div className="card card-compact bg-base-100 w-96 shadow-xl">
  <figure>
    <img
      src={image}
      alt="FoodCard" />
  </figure>
  <p className='bg-slate-900 text-white absolute right-0 mr-4 mt-4 px-4'>${price}</p>
  <div className="card-body flex flex-1 items-center">
    <h2 className="card-title">{name}</h2>
    <p>I{recipe}</p>
    <div className="card-actions justify-end">
      <button onClick={() =>handleAddToCart(item)} className="btn btn-outline bg-slate-100 border-orange-400 uppercase border-0 border-b-4 mt-10">Add TO Card</button>
    </div>
  </div>
</div>
       </div>
    );
}; 

export default FoodCard;
```
## Client side
```jsx
  const handleSignUp = async e => {
    e.preventDefault()
    const form = e.target
    const email = form.email.value
    const name = form.name.value
    const photo = form.photo.value
    const pass = form.password.value
    const regUser ={email, pass, photoURL: photo, displayName: name, role:'user'}
    try {
      // User Register
      const {data} = await axios.post(`${import.meta.env.VITE_API_URL}/signup`,
        regUser
    )
    if(data?.acknowledged==true){
              toast.success('Item Registered Successfully!')
              setUser(regUser)
              navigate('/')
            }else{
              toast.success(data?.message)
              // navigate('/')
            }
} catch (err) {
      console.log(err)
      toast.error(err?.message)
    }
  }
```
