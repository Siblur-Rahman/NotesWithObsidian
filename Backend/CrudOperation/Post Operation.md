```jsx
// PracticeAll with React 
        app.post('/user', async (req, res) => {

          const {password, email} = req.body

          const query = {pass:password, email:email}

          const result = await usersCollection.findOne(query)

          res.send(result)

        })
```
```jsx
// PracticeAll with React
        app.post('/signup', async (req, res) => {

          const userData = req.body

          const query = { email: userData.email };

          const existingUser = await usersCollection.findOne(query);

          if (existingUser) {

            return res.send({ message: "user already exists", insertedId: null });

          }

          const result = await usersCollection.insertOne(userData)

          res.send(result)

        })
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
