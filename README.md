# LIFT (Updating)


Thanks for all of you for your interest in our work.

This project contains the code of LIFT and welcomes contributions or suggestions.

## Compile & Run

```bash
mkdir build
cd build
cmake ..
make
```

- Run example:

```bash
./build/example_lift
```


## Usage

`src/examples/example_lift.cpp` demonstrates the usage of LIFT:


```bash
#include <iostream>
#include <lift.h>

using namespace std;

int main() {
  lift::LIPP <int, int> lift;
  int key_num = 1000;
  pair<int, int> *keys = new pair<int, int>[key_num];
  for (int i = 0; i < 1000; i++) {
    keys[i]={i,i};
  }
  lift.bulk_load(keys, 1000);

  for (int i = 1000; i < 2000; i++) {
    lift.insert(i,i);
  }
  for (int i = 0; i < 2000; i++) {
    bool exist;
    auto result = lift.at(i, false, exist);
    if (exist) {
        std::cout << "value at " << i << ": " << result << std::endl;
    } else {
        std::cout << "value at " << i << ": not found" << std::endl;
    }
  }
  std::cout << " over " << std::endl;
  return 0;
}
```

## Running benchmark

LIFT's performance can be assessed using the GRE benchmarking tool. We have integrated LIFT into GRE as "[GRE_LIFT](https://github.com/WHIndex/GRE_LIFT)", which is a fork of GRE. In GRE_LIFT, you can assess the performance of LIFT comprehensively. Additionally, the concurrent version of LIFT, LIFTOL, is also included in GRE_LIFT, and can be found at "[LIFTOL](https://github.com/WHIndex/liftol)".



## License

This project is licensed under the terms of the MIT License.