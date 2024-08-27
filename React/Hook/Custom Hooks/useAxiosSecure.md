```jsx
import axios from "axios";
import { useEffect } from "react";
import useAuth from './useAuth';
import { useNavigate } from "react-router-dom";

const axiosSecure = axios.create({
    baseURL:`${import.meta.env.VITE_API_URL}`,
    withCredentials: true,
})
const useAxiosSecure = () => {
    const {logOut} = useAuth();
    const navigate =useNavigate()
    useEffect( () =>{
        axiosSecure.interceptors.response.use(res =>{
            return res;
        }, error =>{
            console.log('error tracked in the interceptor', error.response)
            if(error.response.status === 401 || error.response.status=== 403){
                console.log('logout the user')
                logOut()
                .then(() =>{
                    navigate('/login')
                })
                .catch( error => console.log(error))
            }
        })
    }, [])

    return axiosSecure;
};
export default useAxiosSecure;
```
## useAxiosSecure Hook for get data
From 
```jsx
const axiosSecure = useAxiosSecure()
    // const url = `http://localhost:5000/bookings?email=${user?.email}`;
    const url = `/bookings?email=${user?.email}`;
    useEffect(() => {
        axiosSecure.get(url)
        .then(res => setBookings(res.data))
    }, [url, axiosSecure]);
```