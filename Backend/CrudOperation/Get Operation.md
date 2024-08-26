
### Client side
#### Get API with fetch

```jsx
    useEffect(()=>{
        fetch(`${import.meta.env.VITE_API_URL}/items/${id}`)
        .then(res=>res.json())
        .then(data=>{
            setItems(data)
        })
    },[items])
    
<Link to={'/updateitem/doller{item._id}'}><button>Update</button></Link>
```
## Get API with axios
```jsx
    const [item, setItem] = useState([])
    const {id} = useParams();
  useEffect(()=>{
     const getData = async() =>{
        const {data} = await axios(`${import.meta.env.VITE_API_URL}/item/${id}`)
        setItem(data)
     };
     getData()
    })
```
## #link

```jsx
<Link to={`/updateitem/${item._id}`}><button>Update</button></Link>
```
## Server

```jsx
    app.get('/allitems', async (req, res) => {

      const result = await itemsCollection.find().toArray()

      res.send(result)

    })
```
