## click on Clear

``` jsx
import { useState } from "react";


const ClickClear = () => {
    const [someText , setSomeText] = useState("");
    const changeInputText = (event) => {
        setSomeText(event.target.value)
    }

    const handleClick = () => {
        setSomeText("")
    }
    return (
        <div>
            <input type="text" className="border border-black" onChange={changeInputText} value={someText} />
            <br />
            <button className="border border-black bg-gray-300" onClick={handleClick}>Clear</button>
        </div>
    )
} 

export default ClickClear;
```

## add dictionary items and key will be auto generated from 1, 2, 3...

``` jsx
import { useState } from "react"

const AddItemDictionary = () =>{
    const [someItem, setSomeItem] = useState("")
    const [counter, setCounter] = useState(1)
    const [dictionary, setDictionary] = useState({})
    const addItemChange = (event) =>{
        setSomeItem(event.target.value)

    }
   
    const addClick = () => {
        if (someItem.trim()){

            const newKey = counter.toString();
            setDictionary((item) => ({
                ...item,
                [newKey]:someItem
            }))
        }
        
        setSomeItem("")
        setCounter(counter+1)
        // console.log(dictionary)
       
    }

    return (
        <div className="m-1">
            <input type="text" className="border border-black" onChange={addItemChange} value={someItem} />
            <br />
            <button className="border border-gray-600 bg-gray-100" onClick={addClick}>Add or Edit</button>
            
                {Object.keys(dictionary).length ===0 ? (<p>No items added</p>):(
                    <ul>
                          {
                            Object.entries(dictionary).map(([dictKey, dictValue])=> (
                                <li key={dictKey}>{dictValue}</li>
                            ))
                          }  
                    </ul>)}
 
        </div>
    )
}

export default AddItemDictionary
```

## Render:

Rendering in React is the process where React components describe what the UI should look like based on their current state and props. This involves creating a virtual representation of the UI, which React then updates in the actual DOM to reflect any changes.

## SetState() 

SetState() is a method in React used to update the state of a component, which triggers a re-render of that component to reflect the changes in the user interface. It allows React to efficiently manage and render updates without directly manipulating the DOM.

## view = function(state)

when state changes and react re-runs (re-renders) your component, something new gets returned and replaces what used to be on the page.

## changing items in object on click:

``` jsx
import { useState } from "react";
import { FaStar } from "react-icons/fa";
import { FaRegStar } from "react-icons/fa";

const ContactCard = () => {
    const [contact, setContact] = useState({
        firstName: "John",
        secondName: "Doe",
        phone: "9484329383",
        email: "johndoe@example.com",
        isFavourite: false
    })
    const toggleFavourite = () => {
        setContact(prevContact => {
            return {
                ...prevContact,
                isFavourite : !prevContact.isFavourite
            }
        })
    }
    return (
        

    <div
        className="max-w-2xl mx-4 sm:max-w-sm md:max-w-sm lg:max-w-sm xl:max-w-sm sm:mx-auto md:mx-auto lg:mx-auto xl:mx-auto mt-16 bg-white shadow-xl rounded-lg text-gray-900">
        <div className="rounded-t-lg h-32 overflow-hidden">
            <img className="object-cover object-top w-full" src='https://images.unsplash.com/photo-1549880338-65ddcdfd017b?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=400&fit=max&ixid=eyJhcHBfaWQiOjE0NTg5fQ' alt='Mountain' />
        </div>
        <div className="mx-auto w-32 h-32 relative -mt-16 border-4 border-white rounded-full overflow-hidden">
            <img className="object-cover object-center h-32" src='https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=400&fit=max&ixid=eyJhcHBfaWQiOjE0NTg5fQ' alt='Woman looking front' />
        </div>
        <div className="text-center mt-2">
            <h2 className="font-semibold">{contact.firstName} {contact.secondName}</h2>
            <p className="text-gray-500">Freelance Web Designer</p>
            <p>{contact.phone}</p>
            <p className="text-gray-500">{contact.email} </p>
        </div>
        <ul className="py-4 mt-2 text-gray-700 flex items-center justify-around">
            <li className="flex flex-col items-center justify-around cursor-pointer " onClick={toggleFavourite}>
                {contact.isFavourite? <FaStar /> : <FaRegStar />}
                <div>2k</div>
            </li>
            <li className="flex flex-col items-center justify-between">
                <svg className="w-4 fill-current text-blue-900" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                    <path
                        d="M7 8a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm0 1c2.15 0 4.2.4 6.1 1.09L12 16h-1.25L10 20H4l-.75-4H2L.9 10.09A17.93 17.93 0 0 1 7 9zm8.31.17c1.32.18 2.59.48 3.8.92L18 16h-1.25L16 20h-3.96l.37-2h1.25l1.65-8.83zM13 0a4 4 0 1 1-1.33 7.76 5.96 5.96 0 0 0 0-7.52C12.1.1 12.53 0 13 0z" />
                </svg>
                <div>10k</div>
            </li>
            <li className="flex flex-col items-center justify-around">
                <svg className="w-4 fill-current text-blue-900" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                    <path
                        d="M9 12H1v6a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-6h-8v2H9v-2zm0-1H0V5c0-1.1.9-2 2-2h4V2a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v1h4a2 2 0 0 1 2 2v6h-9V9H9v2zm3-8V2H8v1h4z" />
                </svg>
                <div>15</div>
            </li>
        </ul>
        <div className="p-4 border-t mx-8 mt-2">
            <button className="w-1/2 block mx-auto rounded-full bg-gray-900 hover:shadow-lg font-semibold text-white px-6 py-2">Follow</button>
        </div>
    </div>
    )
}

export default ContactCard;
```
