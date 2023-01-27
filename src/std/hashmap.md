# `HashMap`

Standard hash map with protection against HashDoS attacks:

```rust,editable
use std::collections::HashMap;

fn main() {
    let mut page_counts = HashMap::new();
    page_counts.insert("Adventures of Huckleberry Finn".to_string(), 207);
    page_counts.insert("Grimms' Fairy Tales".to_string(), 751);
    page_counts.insert("Pride and Prejudice".to_string(), 303);

    if !page_counts.contains_key("Les Misérables") {
        println!("We've know about {} books, but not Les Misérables.",
                 page_counts.len());
    }

    for book in ["Pride and Prejudice", "Alice's Adventure in Wonderland"] {
        match page_counts.get(book) {
            Some(count) => println!("{book}: {count} pages"),
            None => println!("{book} is unknown.")
        }
    }
}
```

<details>
* Point out that `HashMap` is not in the prelude and it needs to brought into scope
* In a hashmap, types with the Copy trait (i32) are copied into the hashmap while owned values (String) are moved into the hashmap.
* You can demonstrate different variations of unwrapping and print the results. Only the later changes the value in the hashmap.
```  
    page_counts.get("HP").unwrap_or(&336);
    age_counts.entry("The Hunger Games".to_string()).or_insert(374);
```
    
</details>
