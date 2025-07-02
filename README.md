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
