# React TS
## Create React TypeScript project
That is support for type definations to JavaScript code bases.
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
If we explicit component as ReactComponent that will auto receive content as children without declare the children params in props.
4. State with TypeScript
`const [name, setName] = useState('your default value');`
5. Type inference with state
`const [guests. setGuests] = useState<string[]>([])
 setGuests([...guests, name])
`
6.  TypeUnicons in State
`const[user, setUser]` = useState<{name: String, age: number} | undefined>

## Section 3. - Type around Events and Refs
1. Event:
All type can be refer in there html suggestion.
2. TS with Class Component.

`Class UserSeach extends Component<UserSeachProps> {
}`


=> Apply TS => Apply types to components props, type to state of component, type for event handlers and other assorted areas
3. Refs






