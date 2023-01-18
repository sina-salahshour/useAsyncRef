# React useAsyncRef hook

- this hook works exactly like useRef hook, but it has an additional field called `asyncCurrent`
- that returns a promise, that gets resolved when the ref gets a value other than null | undefined.

example usage:

```tsx
const Component = () => {
  const nameRef = useAsyncRef<HTMLInputElement>(null)
  const descRef = useAsyncRef<HTMLInputElement>(null)
  const submit = async () => {
    const textCurrent = await nameRef.asyncCurrent
    const text2Current = await descRef.asyncCurrent
    console.log('name', textCurrent.value)
    console.log('desc', text2Current.value)
  }
  return (
    <div>
      <p>name</p>
      <input className="text-black" ref={nameRef} type="text" />
      <p>desc</p>
      <input className="text-black" ref={descRef} type="text" />
      <button onClick={submit}>submit</button>
    </div>
  )
}
```
