# click on Clear

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
