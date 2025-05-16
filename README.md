# To-do-list
first github repository,

function App() {
  const[inputText,setInputText]= useState("");
  const[items,setItems]=useState([]);

  function handleChange(event){
    const newValue=event.target.value;
    setInputText(newValue);
  }

  function addItem(event) {
    if(!items.includes(inputText)){
     setItems(prevItems => {
      return [...prevItems, inputText];
    }); 
    }
    else{
      alert("Task already exists")
    }
    
    setInputText("");
  }
  function deleteItem(id){
    setItems((prevItems) => {
      return prevItems.filter((items,index)=>{
        return index!==id;
      });
    });
  }

  return(
    <div className='container'>
      <div className='heading'>
        <h1>To-Do List</h1>
      </div>
      <div className='form'>
        <input onChange={handleChange} type="text" placeholder="Add Task" value={inputText}/>
        <button onClick={addItem}>
          <span>Add</span>
        </button>
      </div>
      <div className='listitems'>
        <ul>
          {items.map((todoItem,index) => 
            (<TodoItem 
              key={index} 
              id={index} 
              text={todoItem} 
              unChecked={deleteItem}/>
            ))}
        </ul>
      </div>
    </div>
  )
}
