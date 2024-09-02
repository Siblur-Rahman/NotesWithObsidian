```jsx
const [services, setServices] = useSate([])
    useEffect(() => {
        fetch(`${import.meta.env.VITE_API_URL}/services`)
            .then(res => res.json())
            .then(data => setServices(data));
    }, [])
```