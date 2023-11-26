# React TS

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
1. Use union type to define that as a mode to switch the behaviors.
2. Discriminated Unions
```ts
type HintBoxProps = {
   mode: 'hint';
   children: ReactNode
}
type WarningBoxProps = {
   mode: 'warning';
   severity: 'low' | 'medium' | 'high';
   children: ReactNode
}
type InfoBoxProps = HintBoxProps | WarningBoxProps;
```
3. Wrapper Component




