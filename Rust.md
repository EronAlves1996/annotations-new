
* In Rust, make some experiment about value types and reference types is like loose some time, because it don't happens to have any overhead to acessing values for value type and reference type.
* When build as release, we note a minimal overhead for a reference type.
* For boxed numbers and boxed value type, minimal overhead as else
```rust
use std::{
    fmt::Display,
    ops::{Add, Deref, Sub},
    time::Instant,
};

struct Point {
    x: i32,
    y: i32,
}

impl Add for Point {
    type Output = Point;

    fn add(self, rhs: Self) -> Self::Output {
        Point {
            x: self.x + rhs.x,
            y: self.y + rhs.y,
        }
    }
}

impl Sub for Point {
    type Output = Point;

    fn sub(self, rhs: Self) -> Self::Output {
        Point {
            x: self.x - rhs.x,
            y: self.y - rhs.y,
        }
    }
}

impl Display for Point {
    fn fmt(&self, f: &mut std::fmt::Formatter<'_>) -> std::fmt::Result {
        write!(f, "[x: {}, y: {}]", self.x, self.y)
    }
}

struct PointAllReference {
    x: Box<i32>,
    y: Box<i32>,
}

impl Add for PointAllReference {
    type Output = Box<PointAllReference>;

    fn add(self, rhs: Self) -> Self::Output {
        Box::new(PointAllReference {
            x: Box::new(self.x.add(rhs.x.deref())),
            y: Box::new(self.y.add(rhs.y.deref())),
        })
    }
}

fn main() {
    println!("Test comparison for value types and reference types");
    println!("Let's define a Point type, like this:");
    let point = Point { x: 5, y: 6 };
    let point_reference = Box::new(Point { x: 5, y: 6 });
    println!("{point}");
    println!("I already have instantiate this same point as a reference type and as a value type");
    println!("Let's compare access to underlying values");
    let start = Instant::now();
    println!("Reference type access");
    println!("{}", &point_reference.y);
    println!("Acessed in {}", start.elapsed().as_micros());
    let start = Instant::now();
    println!("Value type access");
    println!("{}", point.x);
    println!("Acessed in {}", start.elapsed().as_micros());
    println!("Doing some operations, adding two reference type pointers");
    let other_reference = Box::new(Point { x: 6, y: 7 });
    let start = Instant::now();
    println!("{}", &(&point_reference.add(*other_reference)));
    println!("Execute in {}", start.elapsed().as_micros());
    println!("Adding two value types");
    let other = Point { x: 6, y: 7 };
    let start = Instant::now();
    println!("{}", point + other);
    println!("Execute in {}", start.elapsed().as_micros());
    println!("If we perform some all boxed operations??");
    let p = Box::new(PointAllReference {
        x: Box::new(5),
        y: Box::new(6),
    });
    let o = Box::new(PointAllReference {
        x: Box::new(6),
        y: Box::new(8),
    });
    let start = Instant::now();
    let _s = &p.add(*o);
    println!("Execute in {}", start.elapsed().as_micros());
}
```
* Maybe in Java it probably can represent a overhead, because it's a VM that controls the stack, vs allocating it in plain binary in Rust. So, this exercise could be useless to be made in rust