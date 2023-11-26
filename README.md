# React TS (https://react.dev/reference/react)

**Motivation** : Get the type safety to your JavaScript code

**Solution**: Typescriot builds up on JavaScript and extends its syntax by adding strong typing.

## Create React TypeScript project

**Create react ts project** `npx create-react-app <app-name> --template typescript`

**You'd like use typescript for old react project** - please add 2 libs `@types/react` and `@types/react-dom` to get full React Web support.

**Compiler options** need to be set in `tsconfig.json`

#### Extensions
- File contains a ReactComponent or kind of JSX => `.tsx`
- TypeScript only => `.ts`

## Section 2 - Type Around Props and State

1. Props
  Props is arguments passed into React Components, It was passed by HTML attributes.
2. Explicit Component Type Annotation
   Code like a normal function that is not meaning of ReactComponent => we should explicit Component
   `
   export const Child: React.FC<ChildProps> = ({color}) => {}
   `
3. Anotation with Children
If we explicit component as ReactComponent that will auto receive content as children without declare the `children` params in props.
if not you have to declare the `children` params `{children: ReactNode}`
4. State with TypeScript
Listent state of a variable
```ts
const [name, setName] = useState('your default value');`
```
5. Type inference with state
```ts
const [guests. setGuests] = useState<string[]>([])
 setGuests([...guests, name])
```
6.  TypeUnicons in State
```ts
const[user, setUser]` = useState<{name: String, age: number} | undefined>
```
7. useEffect
   Do when some field was change, default run first time
```ts
useEffect(() => {//do something }, [])
``` 
## Section 3. - Type around Events and Refs
1. Event:
All type can be refer in there html suggestion.
2. TS with Class Component.

`Class UserSeach extends Component<UserSeachProps> {
}`


=> Apply TS => Apply types to components props, type to state of component, type for event handlers and other assorted areas

3. Refs
To referent a variable to a HTML element

```ts
const inputRef = useRef<HTMLInputElement | null>();
<input ref={inputRef} />
```
We can work with `input` element through `inputRef`

The variable is observated in second param, in this case second param is [] => just run in the first time.

## Section 4 - Advanced Component Types - Dynamic Components, Polymorphic Components and Mores.
1. Use union type to define that as a mode to switch the behaviors as Discriminated Unions
```ts
type HintBoxProps = {
   mode: 'hint'; //can use for switch in if else of react component type script
   children: ReactNode
}
type WarningBoxProps = {
   mode: 'warning';
   severity: 'low' | 'medium' | 'high';
   children: ReactNode
}
type InfoBoxProps = HintBoxProps | WarningBoxProps;
```
2. Wrapper Component
You can wrapper component as a customized component.
```ts
type InputProps = ComponentPropsWithoutRef<'input'> & {id: string}
export const Input: React.FC<InputProps> = ({id, ...attributes}) => {
  return <input className='button' id={id} {...atrributes} /> //can add more strategy
} //all input atrributes take over to this custom Input 
```

```?``` is optional variable
3. Polymorphic Component.
```ts
type ContainerProps<T extends ElementType> = {
as?: T;
childrent: ReactNode; } & ComponentPropsWithoutRef<T>

export default function Container<C extends ElementType> ({as, childrent, ...props} : ContainerProps<C>) {
const Component = as | 'div';
return <Component className='container' {...props}>{childrent}</Component>
}
```
4. List
```ts
    <List
      items={hobbies}
      renderItem={(hobby) => <li key={hobby}>{hobby}</li>}
    />
```
5. `forwardRef
 If you would like to pass your ref to your custom element, that should use forwardRef
```ts
const Input = forwardRef<HTMLInputElement, InputProps>( function Input<{id, ...props}> : InputProps, ref {
return <input id={id} {...props} ref={ref} />
})
```
6. Form custom component
   
```ts
type FormProps = ComponentPropsWithoutRef<'form'> & {
onSave: (value: unknown) => void
};
export default function Form({onSave, childrent, ...otherProps}) {
const form = useRef<HTMLFormElement>(null)

// @Link: https://react.dev/reference/react/useImperativeHandle
useImperativeHandle(ref, () => { //idea is expose a ref from parent to this component then interact with that ref - we call that is expose Component API.
  return {
    clear() {
      form.current?.rest();
    }
  }
}) // In this we expose a the clear API way which should be refer from parent. Need to practice

const handleSubmit: (event: FormEvent<HTMLFormElement>) => {
  event.preventDefault();
  const formData = new FormData(event.curentTarget);
  const data = Object.fromEntries(formData);
  onSave(data);
  form.current?.reset();
}
  return <form {...otherProps} ref={form}>{childrent}</form>
}
```
7. 




