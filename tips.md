## C++

---------------------------------------------------------------------------

# Initialization:

**don't ever us this**

    auto x = {n} | int y = {n}

*use **this** instead*

    std::initializer_list<int> x = {n}


####

*some initilaization rules:*
    
    vector<int> x{10}      // one element - value = 10
    vector<int> y(10, 20)  // 10 elements - value = 20
    vector<int> z = 1      // Error. no conversion from int to vector


    void f(const vector<double>&);

    void g()
    {
        v1 = 9; // error : no conversion from int to vector
        f(9);   // error : no conversion from int to vector
    }

    // By replacing " () " and " = "  w/ {} we get:
    void g()
    {
        v1 = {9}; // OK: v1 now has one element (with the value 9)
        f({9});   // OK: f is called with the list {9}
    }


---------------------------------------------------------------------------

# Limits

**max Double**

    double d = DBL_MAX

**max float**

    float d = FLT_MAX

*these are defined in < climits >*

**max long double**

    long double d = numeric_limits<long double>::max();

*max() is defined in < limits >*

---------------------------------------------------------------------------

# Conversion / Casting

**Pointer, integral and floating-point values can be implicitly converted to bool**
*a nonzero value converts to true and zero value converts to false*

    /* e.g: */
    void f (int* p, int i) {
       
       bool is_not_zero = p; // true if p!=0
       bool b2 = i; // true if i!=0
    }

**u can convert pointer to const pointer and reference to const reference implicitly**

---------------------------------------------------------------------------

# Errors

**throw runtime error**
    
    if (1 != 2)
     throw std::runtime_error{"What am i crazy");

---------------------------------------------------------------------------

# Operators


|               `USE`                    |                 `SYNTAX`                |       `REFERENCE`      |
|----------------------------------------|:----------------------------------------|-----------------------:|                     
|   Subscripting                         |  pointer −> member                      |        §16.2.3         |
|   Member selection                     |  pointer [ expr ]                       |        §7.3            |
|   Function call                        |  expr ( expr-list )                     |        §12.2           |
|   Value construction                   |  type { expr-list }                     |        §11.3.2         |
|   Function-style type conversion       |  type ( expr-list )                     |        §11.5.4         |
|   Post increment                       |  lvalue ++                              |        §11.1.4         |
|   Post decrement                       |  lvalue −−                              |        §11.1.4         |
|   Type identification                  |  typeid ( type )                        |        §22.5           |
|   Run-time type identification         |  typeid ( expr )                        |        §22.5           |
|   Run-time checked conversion          |  dynamic_cast < type > ( expr )         |        §22.2.1         |
|   Member selection                     |  object . member                        |        §16.2.3         | 
|   Compile-time checked conversion      |  static_cast < type > ( expr )          |        §11.5.2         |
|   Unchecked conversion                 |  reinterpret_cast < type > ( expr )     |        §11.5.2         |
|   const conversion                     |  const_cast < type > ( expr )           |        §11.5.2         |
|   Size of object                       |  sizeof expr                            |        §6.2.8          |
|   Size of type                         |  sizeof ( type )                        |        §6.2.8          |
|   Size of parameter pack               |  sizeof... name                         |        §28.6.2         |
|   Alignment of type                    |  alignof ( type )                       |        §6.2.9          |
|   Pre increment                        |  ++ lvalue                              |        §11.1.4         |
|   Pre decrement                        |  −− lvalue                              |        §11.1.4         |
|   Complement                           |   ̃ expr                                 |        §11.1.2         |
|   Not                                  |  ! expr                                 |        §11.1.1         |
|   Unary minus                          |  − expr                                 |        §2.2.2          |
|   Unary plus                           |  + expr                                 |        §2.2.2          |
|   Address of                           |  & lvalue                               |        §7.2            |
|   Dereference                          |  ∗ expr                                 |        §7.2            |
|   Create (allocate)                    |  new type                               |        §11.2           |
|   Create (allocate and initialize)     |  new type ( expr-list )                 |        §11.2           |
|   Create (allocate and initialize)     |  new type { expr-list }                 |        §11.2           |
|   Create (place)                       |  new ( expr-list ) type                 |        §11.2.4         |
|   Create (place and initialize)        |  new ( expr-list ) type ( expr-list )   |        §11.2.4         |
|   Create (place and initialize)        |  new ( expr-list ) type { expr-list }   |        §11.2.4         |
|   Destroy (deallocate)                 |  delete pointer                         |        §11.2           |
|   Destroy array                        |  delete [] pointer                      |        §11.2.2         |
|   Can expression throw?                |  noexcept ( expr )                      |        §13.5.1.2       |
|   Cast (type conversion)               |  ( type ) expr                          |        §11.5.3         |
|   Member selection                     |  object .∗ pointer-to-member            |        §20.6           |
|   Member selection                     |  pointer −>∗ pointer-to-member          |        §20.6           |
|                                        |                                         |                        |
|   Multiply                             |  expr ∗ expr                            |        §10.2.1         |
|   Divide                               |  expr / expr                            |        §10.2.1         |
|   Modulo (remainder)                   |  expr % expr                            |        §10.2.1         |
|   Add (plus)                           |  expr + expr                            |        §10.2.1         |
|   Subtract (minus)                     |  expr − expr                            |        §10.2.1         |
|   Shift left                           |  expr << expr                           |        §11.1.2         |
|   Shift right                          |  expr >> expr                           |        §11.1.2         |
|   Less than                            |  expr < expr                            |        §2.2.2          |
|   Less than or equal                   |  expr <= expr                           |        §2.2.2          |
|   Greater than                         |  expr > expr                            |        §2.2.2          |
|   Greater than or equal                |  expr >= expr                           |        §2.2.2          |
|   Equal                                |  expr == expr                           |        §2.2.2          |
|   Not equal                            |  expr != expr                           |        §2.2.2          |
|   Bitwise and                          |  expr & expr                            |        §11.1.2         |
|   Bitwise exclusive-or                 |  expr ˆ expr                            |        §11.1.2         |
|   Bitwise inclusive-or                 |  expr | expr                            |        §11.1.2         |
|   Logical and                          |  expr && expr                           |        §11.1.1         |
|   Logical inclusive or                 |  expr || expr                           |        §11.1.1         |
|   Conditional expression               |  expr ? expr : expr                     |        §11.1.3         |
|   List                                 |  { expr-list }                          |        §11.3           |
|   Throw exception                      |  throw expr                             |        §13.5           |
|   Simple assignment                    |  lvalue = expr                          |        §10.2.1         |
|   Multiply and assign                  |  lvalue ∗= expr                         |        §10.2.1         |
|   Divide and assign                    |  lvalue /= expr                         |        §10.2.1         |
|   Modulo and assign                    |  lvalue %= expr                         |        §10.2.1         |
|   Add and assign                       |  lvalue += expr                         |        §10.2.1         |
|   Subtract and assign                  |  lvalue −= expr                         |        §10.2.1         |
|   Shift left and assign                |  lvalue <<= expr                        |        §10.2.1         |
|   Shift right and assign               |  lvalue >>= expr                        |        §10.2.1         |
|   Bitwise and and assign               |  lvalue &= expr                         |        §10.2.1         |
|   Bitwise inclusive-or and assign      |  lvalue |= expr                         |        §10.2.1         |
|   Bitwise exclusive-or and assign      |  lvalue ˆ= expr                         |        §10.2.1         |
|   comma (sequencing)                   |  expr , expr                            |        §10.3.2         |
|                                        |                                         |                        |

#

##`Token Summery`

|               `Token Class`            |                 `Example`               |       `REFERENCE`      |
|----------------------------------------|:----------------------------------------|-----------------------:|
|   Character literal                    |  vector , foo_bar , x3                  |        §6.3.3          |
|   Integer literal                      |  int , for , virtual                    |        §6.3.3.1        |
|   Identifier                           |  ’x’ , \n’ , ’U’\UFADEFADE’             |        §6.2.3.2        |
|   Floating-point literal               |  12 , 012 , 0x12                        |        §6.2.4.1        |
|   Keyword                              |  1.2 , 1.2e−3 , 1.2L                    |        §6.2.5.1        |
|   String literal                       |  "Hello!" , R"("World"!)"               |        §7.3.2          |
|   Operator                             |  += , % , <<                            |        §10.3           |
|   Punctuation                          |  ; , , , { , } , ( , )                  |                        |
|   Preprocessor notation                |  # , ##                                 |        §12.6           |

#

##`Alternative Representation`

|   `TYPEDEF`     |     `OPERATOR`      |
|-----------------|---------------------|
|   and           |         &           |
|                 |                     |
|   and_eq        |         &=          |
|                 |                     |
|   bitand        |         &           |
|                 |                     |
|   bitor         |         \|          |
|                 |                     |
|   compl         |         ~           |
|                 |                     |
|   not           |         !           |
|                 |                     |
|   not_eq        |         !=          |
|                 |                     |
|   or            |         \|\|        |
|                 |                     |
|   or_eq         |         \|=         |
|                 |                     |
|   xor           |         ^           |
|                 |                     |
|   xor_eq        |         ^=          |
|                 |                     |


##Shortcut to copy strings

    while (∗p++ = ∗q++);


# Function Pointer

    void doSome(int a) {
        std::cout << "Do something w/ " << a << '\n';
    }

    // Initialize
    void (*doPtr)(int) = &doSome;

    // Invoke
    (*doPtr)(12);

    // Output
    Do something w/ 12

    /*
         Without " & " and " * " 
    */
    void (*doPtr)(int) = doSome;
    doPtr(12);

    // Output
    Do something w/ 12

    /*
        Array of functions
    */

    void doSome(int a) {
    std::cout << "Do something 0 w/ " << a << '\n';
    }

    void doSome1(int a)
    {
        std::cout << "Do something 1 w/ " << a << '\n';
    }

    void doSome2(int a)
    {
        std::cout << "Do something 2 w/ " << a << '\n';
    }

    std::cout << "Enter Choice: \n" << "0. doSome\t 1. doSome1\t 2. doSome2" << '\n';
    ch = getch()    // in huncho.h
    
    ch -= '0';  // convert const char to int const

    doPtr[ch](12); // invoke function by index


# OS  MACROS C/C++

    _WIN32          // Windows 32 Bit
    _WIn64          // Windows 64 Bit
    __unix          // Unix
    __unix__        // Unix
    __APPLE__       // Apple
    __MACH__        // Mac OS
    __LINUX__       // Linux
    __FreeBSD__     // Free BSD

------------------------------------

    // e.g:

    std::string getOs() {

        #ifdef _WIN32
            return "Windows 32-bit";

        #elif _WIN64
            return "Windows 64-bit;

        #elif _unix || __unix__
            return "Unix";

        #elif __APPLE__ || __MACH__
            return "Mac OSx";

        #elif __LINUX__
            return "Linux";

        #elif _FreeBSD__
            return "FreeBSD";

        #else 
            return "Other";

        #endif
        
    }


# Casting Types

## Static Cast

this is a compile time cast and does things like implicit conversion between types (int, float or pointer to void* and it can also call explicit conversion fuctions) (or implicit ones).

    //e.g:
    float a = 12.99;
    int b = static_cast<int>(a);

    // w/ *'s
    int i = 12;
    void *p = static_cast<void *>(&i); 
    int *x = static_cast<int *>(p);


## Const Cast

const cast is used to cast away the constness of variable, const cast can be used to change non-const class members inside a function, const cast can be used to pass const data to a function that doesn't allow const

    //e.g:

    int f (int* p) {
        return (*ptr + 10);
    }

    const int val = 10;
    const int *p = &val;

    // u cannot modify the calue here
    int *pf = const_cast<int *>(p);

    std::cout << f(pf);

    // if u wanna modify the value make int val non const:
    int val = 10;

    // same as above...


## Dynamic Cast

dynamic cast works at runtime rather than compile time like static cast, DC can work only in polymorphic types

    strutc A {
        virtual void f();
    };
    struct B : public A {};
    struuct C {};


    A a;
    B b;

    A *ap = &b;
    B *b1 = dynamic_cast<B *>(&a);       // NULL, bcus 'a' is not 'b'
    B *b2 = dynamic_cast<B *>(ap);       // 'b'
    C *c  = dynamic_cast<C *>(ap);       // NULL

    A& ar = dynamic_cast<A&>(*ap);       // OK.
    B& br = dynamic_cast<B&>(*ap);       // OK.
    C& cr = dynamic_cast<C&>(*ap);       // ERROR: std::bad_cast


## Reinterpret Cast

RC is used to convert one pointer of another pointer of any type, no matter wither the class is related to each other or not. it does not check if the pointer type and the data pointed by the pointer is same or not. and it doesn't have any return type it simply converts the pointer.

***syntax***
    datatype *var_name = reinterpret_cast<data_type *>(pointer variable);


    int *p = new int(64);
    char *cp = reinterpret_cast<char *>(p);

    cout << *p << '\n';     // 64;
    cout << *cp << '\n';    // B;
    cout <<  p << '\n';     // 0x902bf;
    cout <<  ch << '\n';    // A;



# Types of function declerations

- **inline** - indicating a desire to have function calls implemented by inlining the function body    
- **constexpr** - indicating that it should be possible to evaluate the function at compile time if given constant expressions as arguments  
- **noexcept** - indicating that the function may not throw an exception
- **static** - used for linkage specification
- **\[[noreturn]]** - indicating that the function will not return using the normal call/return mechanism
- **virtual** - indicating that it can be overridden in a derived class
- **override** - indicating that it must be overriding a virtual function from a base class
- **final** - indicating that it cannot be overriden in a derived class
- **static** - indicating that it is not associated with a particular object
- **const** - indicating that it may not modify its object 

####

        // Little snippet of what you are getting youself into.
        struct S {
            [[noreturn]] virtual inline auto f(const unsigned long int ∗const) −> void const noexcept;
        };

## You can also define return type of a function like following

    auto f(void) -> int { } // int is a return type of this function.


## Rule of thumb for passing values

- Use pass-by-value for small objects.
- Use pass-by- const -reference to pass large values that you don’t need to modify.
- Return a result as a return value rather than modifying an object through an argument.
- Use rvalue references to implement move and forwarding.
- Pass a pointer if ‘‘no object’’ is a valid alternative (and represent ‘‘no object’’ by nullptr ).
- Use pass-by-reference only if you have to.


## Specify the size of the array while passed it to a fucntion

    void f(int(&arr)[4]); // size = 4

    int arr[] = {1, 2, 3};
    f(arr); // OK.

    int arr2[] = {1, 2, 3, 4};
    f(arr); // Error. size !4


    /*
     * Example w/ template
     *
     */

    template <class T, int N>

    void f(T(&errc)[N]) {

        for (auto& x : errc) 
            std::cout << x << '\n';
    }


    int arr[] = {1, 2, 3, 4};
    f<int, 4>(arr); // OK.

    f(int, 5)(arr); // Error. size != size of the arr



## Ellipsis

**syntax:**
    
    return_type function_name (arg_list, ...)


- The arg_list is one or more normal function parameter
- Function that have ellipsis must have at least one non-ellipsis parameter
- Any parameter passed to the function must match the arg_list parameter first
- ( ... ) must always be the last parameter in the function
- ellipsis are defined in \<cstdrag> header

`Exmaple`

    #include <iostream>
    #include <cstdarg>

    // argc is how many additional args we are passing

    double findAvg(int argc, ...) {

        double sum = 0;

        // we access the ellipsis thru va_list 

        va_list ls;

        // we, initialize the va_list using va_start so,
        // first parameter is : the list to initialize
        // second parameter is : the last non - ellipsis

        va_start(ls, argc);

        // Loop thru all the ellipsis arguements
        for (int i = 0; i < argc; ++i)
            // we use va_arg to get parameters out of our ellipsis
            // First parameter is the va_list we are using
            // Second parameter is the type of the parameter

            sum += va_arg(ls, int);

        va_end(ls);

        return sum / argc;

    }


    int main() {

        std::cout << findAvg(5, 1, 2, 3, 4, 5) << '\n';
        std::cout << findAvg(6, 1, 2, 3, 4, 5, 6) << '\n';

        return 0;
    }


####
    Output: 
    3
    3.5

but this is the shittiest thing you could do u cus type checking aint a thing in this hoe. so, i think we shoul use decoder convention to check for the type

`Example`

    #include <iostream>
    #include <cstdarg>
    #include <string>



    // argc is how many additional args we are passing
    double findAvg(std::string decoder, ...) {

        double sum = 0;

        // we access the ellipsis thru va_list 
        va_list ls;

        // we, initialize the va_list using va_start so,
        // first parameter is : the list to initialize
        // second parameter is : the last non - ellipsis
        va_start(ls, decoder);

        int cnt = 0;

        while (1) {

            char codeType = decoder[cnt];

            switch (codeType)
            {
                default:

                case '\0': 
                    // clean up the va_list when we are done
                    va_end(ls);
                    return sum / cnt;
                    break;

                case 'i':
                    sum += va_arg(ls, int);
                    ++cnt;
                    break;

                case 'd':
                    sum += va_arg(ls, double);
                    ++cnt;
                    break;
                
            }

        }

    }


    int main() {

        std::cout << findAvg("iii", 5, 3, 2) << '\n';
        std::cout << findAvg("iid", 1, 1, 2.3) << '\n';

        return 0;
    }


####
    Output: 
    3.33333
    1.43333


## Some predifined Macros

- `__cplusplus` defined in a C++ cpmpilation (not in C), its value is 201103L
- `__DATE__` date in ***yyyy:mm:dd*** format
- `__TIME__` time in ***hh:mm:ss*** format
- `__FILE__` name of the current source file
- `__FUNC__` an implementation defined C style string, naming the current function
- `__STDC_HOSTED` ***1*** if the implementation hostd, otherwise ***0***
- `__STDC__` defined in C compilation (not in C++)
- `__STDC_MB_MIGHT_NEQ_WC__` ***1*** if, in the encoding for ***wchar_t***, a member of the basic character set might have a code value differs from its value as an ordinary character litteral
- `__STDCPP_STRICT_POINTER_SAFETY__` ***1*** if the implementation has strict pointer safety, otherwise ***undefined***
- `__STDCPP_THREADS` ***1*** if the program can have more than one thread of execution, ohterwise ***undefined***



# Memory measurement chart

| `Data Measurement` |       `Size`          |
|--------------------|-----------------------|
| Bit                |  single bit ( 1 or 0) |
| 1 - Byte           |  8 Bits               |
| 1 - Kilobyte       |  1024 Bytes           |
| 1 - Megabyte       |  1024 Kbs             |
| 1 - Gigabyte       |  1024 Mbs             |
| 1 - Terabyte       |  1024 Gbs             |
| 1 - Petabyte       |  1024 Tbs             |
| 1 - Exhabyte       |  1024 Pbs             |


## Stop Execution of the program for some time

    #include <iostream>
    #include <chrono>
    #include <thread>


    void Matrix() {

        while (1) {

            std::cout << "Doing...\n";
            std::this_thread::sleep_for(std::chrono::seconds(3));
            std::cout << "After 3\n";
        } 
    }
 

# Color and text Prefferences

**`Unix Specific`**

    "\033[1;31m" <cutom text> "\033[0m"
    
####


|  `Color` |  `FG` | `BG`  |
|----------|------:|------:|
| black    |  30   |   40  |
| red      |  31   |   41  |
| green    |  32   |   42  |
| yellow   |  33   |   43  |
| blue     |  34   |   44  |
| magenta  |  35   |   45  |
| cyan     |  36   |   46  |
| white    |  37   |   47  |

####

|  `USE`              |`VAL` |
|---------------------|------|
| reset               |   0 (everything back to how it was)    |        
| bold/bright         |   1  |
| underline           |   4  |
| Inverse             |   7 (swap foreground and background color) |  
| Bold/bright off     |   21 |
| underline/line off  |   24 |   
| inverse off         |   27 |


#

# Get size of console window

**`Windows`**

    #include <windows.h>

    main() {

        CONSOLE_SCREEN_BUFFER_INFO csbi;
        
        GetConsoleScreenBufferInfo(GetSstHandler(STD_OUTPUT_HANDLE), &csbi);

        int cols = csbi.srWindow.Right - csbi.srWindow.Left + 1;    // Width
        int rows = csbi.srWindow.Bottom - csbi.srWindow.Top + 1;    // Height
    }


**`Linux`**

    #include <sys/ioctl.h>
    #include <unistd.h>

    main() {

        struct winsize sz;
        ioctl(STDOUT_FILENO, TIOCGWINSZ, &sz);

        sz.ws_row   // Height
        sz.ws_col   // Width
    }


# Assertions
Assertions are statements used to test assumptions made by programmer, for example we may use assertion to check wether pointer returned by malloc is NULL or not. If the expression evaluates to 0 (false) then expression, sourcode filename, line number are sent thru the stderr and then abort function is called

`Syntax`
    
    void assert( int expression );

*`Example`*

    #include <iostream>
    #include <cassert>

    void main() {

        int x = 7;

        /* some big code here... 
           and lets say x accidently changed to 9
        */

        x = 9;

        // programmer assumes x to be 7 in rest of the code

        assert(x == 7);

    }

#
    // output
    Assertion failed: x == 7, test.cpp, line 13

we can completely ignore assertion statements using **NDEBUG** macro 

    #define NDEBUG
    #include <cassert>


    void main() {

        int x = 7;

        x = 9;

        assert(x == 7);

    }

    // above code compiles and runs fine!



**`static_assert`**

`Syntax`

    static_assert( bool_constexpr , message )      // since c++11
    static_assert( bool_constexpr )      // since c++17

this*  unconditionally checks its condition at comoile time, if the assertion fails compiler writes out the message and compilation fails

    // e.g:

    #include <type_traits>

    template <class T>

    void swap(T& a, T& b) {

        // these is... are defined in < type_traits >
        
        static_assert(std::is_copy_constructable<T>::value, "swap requires copying");
        static_assert(std::is_nothrow_copy_constructable<T>::value && std::is_nothrow_copy_assignable<T>::value, "swap requires nothrow copy/assign");

        auto c = b;
             b = a;
             a = b;
    }

    struct nc {

        nc (const nc& ) = delete;
        nc() = default;
    }

    main() {

        int a, b;
        swap(a, b)      // Ok.

        struct nc nc_a, nc_b;
        swap(nc_a, nc_b);       // assertion faile: message: swap requires copying.
    }


## convert boolean expressions into strings

by default 1 : true and 0 : false so, if wanna get it in a string litteral we can use std::boolalpha

    int b = true;           
    std::cout << b;                       // 1
    std::cout << std::boolalpha << x      // true


## Invoke Functions After Returnting from the main() 

**`atexit(void*());`**

    // is invoked when exit() is called or returned from main 

    // e.g:

    void handler() { std::cout << "Program Terminated\n"; }

    int main() {

        // register the handler
        std::atexit(&handler);

        std::cout << "Returning From main() \n";
        return 0;
    }


####
    //  output
    Returning From main()
    Program Terminated

####

**`at_quick_exit(void(*));`**

    // this bastard is used to fuck w/ quick_exists
    // e.g:

    void handler() { std::cout << "Fuck Yeah Babie!\n"; }

    int main() {

        at_quick_exit(&handler);

        std::cout << "leaving toilet w/t cleaning the shit.\n";

        std::quick_exit(0); // leave toilet w/t cleaning the shit.
    }

####
    // output
    leaving toilet w/t cleaning the shit.
    Fuck Yeah Babie!

###

# explicit 

explicit initialization is also known as direct initialization, A constructor declared with the keyword explicit can only be used for initialization and explicit conversions.

    // e.g:
    class Date {
        int d, m, y;
        public:
        explicit Date(int dd =0, int mm =0, int yy =0);
        // ...
    };

    Date d1 {15};           // OK: considered explicit
    Date d2 = Date{15};     // OK: explicit
    Date d3 = {15};         // error : = initialization does not do implicit conversions
    Date d4 = 15;           // error : = initialization does not do implicit conversions
    

##

# const member functions

The const after the (empty) argument list in the function declarations indicates that these functions do not modify the state of a Class .
in simle words if we got a private memeber for ex. x in const function we cannot modify it for ex. do ++x or x += 1, one thing to remeber bout const functions is that they are read only objects.

    // e.g:

    class Date {
        int d, m, y;
        public:
            int day() const { return d; }
            int month() const { }
            int year() const;

            void add_year(int n);   // add n years
            // ...
    };  

    int Date::year() const
    {
        return ++y; // error : attempt to change member value in const function
    }

    int Date::month const {
        return m + 1    // Ok. just returning m + 1 not messing w/ m's value
    }


imp thing bout the const is that if u make a object const then its functions and shit also has to const member functions ig.

    // e.g:

    class Baw {

        public:
            void smn() { /* ... */}

            void scnd() const { /* ... */ }
    }

    const Baw B;

    B.smn();     // Error: smn is not a const member function
    B.scnd();    // Ok.
        
##

# mutable

mutable is a storage class specifier just like for ex: static, register, extern and auto. Sometimes there is requirement to modify one or more data members of class / struct through const function even though you don’t want the function to update other members of class / struct. This task can be easily performed by using mutable keyword.

    // e.g:

    class Date {
        int d, m;
        mutable int y;

        public:
            int day() const { return d; }
            int month() const { }
            int year() const;

            void add_year(int n);   // add n years
            // ...
    };  

    int Date::year() const
    {
        return ++y; // Ok. we good here, cus its mutable we can fuck w/ it.
    }

    int Date::month const {
        return m += 1    // error : attempt to change member value in const function
    }


## static member

A variable that is part of a class, yet is not part of an object of that class, is called a static member. There is exactly one copy of a static member instead of one copy per object, as for ordinary non- static members Similarly, a function that needs access to members of a
class, yet doesn’t need to be invoked for a particular object, is called a static member function.

    // e.g:

    #include <iostream>

    class F {
        int x;
        static F f;

        public:
            F(int );

            void doit() {
                std::cout <<  x;
            }

            static void smn() {
                std::cout << "i'm static\n";
            }

            static void setDefault(int n) {
                f = {n};    // set default value for F
            }
    };

    F F::f{20};     // set the value of f which would be out default value


    F::F(int s) {
        x = s ? s : 1;
    };

    int main() {

        F x({});
        
        x.doit();   // Ok.

        x.smn();    // Ok.

        F::smn();   // OK.

        F::doit();  // Error: cannot call member function ‘void F::doit()’ without object


        return 0;     
    }

####
    // output: ( aphcourse if we dont do F::doit() )

    20i'm static
    i'm static


###

## print UTF-8 characters to the console

    std::locale old_locale;  // current locale
    setlocale(LC_ALL, "en_US.UTF-8");
    wchar_t w = 0x262F;
    std::wcout << w << std::endl;
    setlocale(LC_ALL, old_locale.name().c_str());

###

## Delegating Constructor

a member-style initializer using the class’s own name (its constructor name) calls another constructor as part of the construction. Such a constructor is called a delegating constructor (and occasionally a forwarding constructor).

    // Ex:
    class X {
        int a;
    public:
        X(int x) { if (0<x && x<=max) a=x; else throw Bad_X(x); }
        X() :X{42} { }
        X(string s) :X{to<int>(s)} { }
    };


###

### `= delete` and `= default`

*default* states that we are allowing the default copy, move or destaructor ( which compiler provides us by defualt ). __If a class has a pointer member, it probably needs a destructor and non-default copy operations__

####Rules: <Magic 5 Statements>

    // lets take an example:

    class Foo {
    public:
        Foo();                      // default constructor
        Foo (Foo& f);               // copy constructor
        Foo (Foo&& f)               // move constructor

        Foo& operator=(Foo& f);     // copy assignment
        Foo& operator=(Foo&& f);    // move assignment

        ~Foo();                     // destructor
    };

####

in example above if we define at least one of em then compiler aint gon generate any of them for us. cus it aint secure.
 
    // if u still want compiler to make em for you, u need to use ' = default

        class Foo {
        public:
            Foo();                      = default
            Foo (Foo& f);               = default
            Foo (Foo&& f)               = default

            Foo& operator=(Foo& f);     = default
            Foo& operator=(Foo&& f);    = default

            ~Foo();                     = default
        };

####

*delete* We can ‘‘delete’’ a function; that is, we can state that a function does not exist so that it is an error to try to use it (implicitly or explicitly).

    // e.g
    class Foo {
        Foo (Foo& f) = delete;      // No copy constructor
    };

    f() {
        Foo f;
        Foo f1 {f}  // Error: no copy constructor
    }


    // we can also use it for functions, for e.g:

    class F {
    public:
        void goo() = delete;
        void foo();
    };

    f() {
        F f;
        f.goo();    // Error: f.goo() deleted
        f.foo();    // Ok.
    }


####
well u might be wondering whats the fucking use of this shit well, lemme halla @ u real quick and tell u that one use case would be to control where the object will be stored like on the `free store` or `stack`.

    // e.g:

    class Not_on_free_store {
        void* operator new (size_t) = delete
    };

    class Not_on_stack {
        ̃ Not_on_stack() = delete;
    };

    void f() {
        Not_on_stack v1;                                    // error : can’t destroy
        Not_on_free_store v2;                               // OK.
        
        Not_on_stack∗ p1 = new Not_on_stack;                // OK.
        Not_on_free_store∗ p2 = new Not_on_free_store;      // error : can’t allocate
    }

    // However, we can never delete that Not_on_stack object. The alternative technique of making the destructor private can address that problem.

##

###**`virtual`** 
is a keyword thats specifies that the function is to be overriden by its derived class. There are two types of virtual functions _virtual_ and _pure virtual_. 
IMP note bout virtual functions is that if u have at least 1 virtual function u need virtual distructor for that.


    // e.g:

    class B {
    public:
        virtual void f() { cout << " in base \n"; } // vitual
        virtual void g() = 0;                       // pure virtual

        virtual ~B();
    };

    void B:g() { cout << "in B \n"; }   // Error: pure virtula function

    class D : B {
    public:
        void f() { cout << " in D \n"; }    
        void g() { cout << " in D \n"; }
    };

###

###**`override`** **`final`**
override and final are whats called a contextual keyword. which means for example if u declare an object or a variable or anything with name **override** or **final** they dont mean nothin compiler is gonna treat em as just name, so to make use of em (what they meant to be used for) u need to declare em at the end of the fucntion that u wanna override. like literally at the end of the function declaration for ex. `void foo() override final {}`.

###override:
so override is a keyword which specifies that the function is gon get overriden. like normally people dont say override when they are overriding a virtual fucntion from the base class. but it looks cool and helps maintian the code.

    // ex:
    
    class B {
        public:
            void foo();
            int override;
    };

    class D : public B {
        public:
            void foo() override { /* mess w/ foo */ }

            override = 12;  // again this override doesnt mean nothin its just name of an int we declared in out base class above.
    };

###final
so, in my opinion final is pretty cool cus it doesnt let u override an object again cus its litteraly final. u feel me? so the idea here is if u got a virtual function in yo base class and u wanna override it but dont want any other classes to fuck w/ it again u use override (exmaple below might explain it better ig.) and if u try to override it BOOM its an erro.

    class B {
        public:
            vitrual void f();
    };

    class D : public B {
        public:
            void f() override final { /* mess w/ f() */ }
    }

    class H : D {
        public:
            void f() override final { /* tryna mess w/ f() */ }     // BOOM its an error. can't override f() cus its declared final above in D.
    }

    // u can make every virtual of a class final, like following:
    class F {
        public:
            virtual void print();
    }

    class G final : public F {          // ok. cool ima make every virtual function in this class final - compiler said!
        public:
            void print() override {}    // ok. cool override it.
    }

    class H : public G {
        void print() override {}        // error: hell nah its final, can't do it!
    }

##Smart Pointers

smart pointers are used to make sure the object is deleted if it is no longer used (refrenced)(e.g: when object goes out of scope) there are basically 2 types of STL smart pointers available for us.

###**unique_ptr**: 
this template holds a pointer to an object and deleted this object when *unique_ptr<>* is deleted. so your lazy ass dont need to explicitly say *delete*, the *unique_ptr* destructor is always called so the element that u stored on the free stored is always deleted s **No Memory Leaks**.

As the name implies make sure only exactly one copy of an object exists. *unique_ptr<>* does not support copying if u try to copy u gon get compile time errors but it supports move semantcis obviously **Note: if a unique pointer already holds pointer to an existing object then that object gets deleted and new pointer is stored e.g: `unique_ptr<int> ptr; ptr.reset( new int{13} );`

The interface that unique_ptr provides is very similar to the ordinary pointer but no pointer arithmetic is allowed. tho this template calss has some helper functions w/ it they dope now u now i'm lazy af. so i aint write em all down here!

**unique_ptr** provides a function called release which yields the ownership. The difference between *release()* and r*eset( )*, is release just yields the ownership and does not destroy the resource whereas reset destroys the resource.

    // Move Example W/ unique_ptr

    #include <iostream>
    #include <memory>
    #include <utility>

    int main() {

        std::unique_ptr<int> ptr( new int{12});
        std::unique_ptr<int> ptr2(std::move(ptr));


        std::cout << "Does ptr hold an object? "
                  << std::boolalpha << static_cast<bool>(ptr) << '\n'
                  << *ptr2 << '\n';   

    }

###**shared_ptr**: 

The shared pointer is a reference counting smart pointer that can be used to store and pass the reference beyond the scope of a function,this is pirtucularly useful int he context of the OOP. to store a pointer as a member variable and return it to access the value outside the scope of the class.

The usage of shared pointer easily pass and return refrence to objects w/t running into memory leaks or invalid attempts to access deleted references "they r thus a cornerstone of modern memory management" - cppreference.com

u can also use std::make_shared<T>() to assign the values and ptr.use_count() to get the reference count.

    #include <iostream>
    #include <memory>

    class Foo {
        public: 
            void dosmn() { std::cout << "SMN()\n"; };
    };

    class Bar {

        public:
            Bar() {
                pfoo = std::shared_ptr<Foo>(new Foo());
            }

            // return shared pointer to Foo object
            std::shared_ptr<Foo> getFoo() { return pfoo; }

        private:
            std::shared_ptr<Foo> pfoo;
    };

    void doSmn() {
        
        Bar* pBar = new Bar();    // w/ the Bar object new Foo is created and stored 
        // reference count = 1

        std::shared_ptr<Foo> pFoo = pBar->getFoo(); // a copy of shared pointer is created
        // reference count = 2

        pFoo->dosmn();

        delete pBar; // with pBar the private pFoo is destroyed
        // reference count = 1

        return; // w/ the return the local pFoo is detsriyed automatically 
        // reference count = 0

        // Internally the std::shared_ptr detsroyes the refernce to the Foo object
    }

    void doSmnElse(std::shared_ptr<Bar> pBar) {

        std::shared_ptr<Foo> pFoo = pBar->getFoo(); // a copy of shared pointer is created
        // reference count = 1

        pFoo->dosmn();

        return; // local pFoo is destroyed
    }

    int main() {

        doSmn();

        std::shared_ptr<Bar> pBar (new Bar);
        doSmnElse(pBar);

    }

by default shared_ptr called delete even if u have an array allocated, so to overcome this problem we can use a lambda.
`std::shared_ptr<int> arr (new int[3], [](int* p) { delete[] p; } );`

###

###**weak_ptr**:
A weak pointer provides sharing semantics and not owning semantics. This means a weak pointer can share a resource held by a shared_ptr. So to create a weak pointer, some body should already own the resource which is nothing but a shared pointer.

A weak pointer does not allow normal interfaces supported by a pointer, like calling *, ->. Because it is not the owner of the resource and hence it does not give any chance for the programmer to mishandle it. Then how do we make use of a weak pointer?

The answer is to create a shared_ptr out of a weak _ptr and use it. Because this makes sure that the resource won't be destroyed while using by incrementing the strong reference count. As the reference count is incremented, it is sure that the count will be at least 1 till you complete using the shared_ptr created out of the weak_ptr. Otherwise what may happen is while using the weak_ptr, the resource held by the shared_ptr goes out of scope and the memory is released which creates chaos.


        void main( )
        {
            shared_ptr<Test> sptr( new Test );  // ref count = 1
            weak_ptr<Test> wptr( sptr );        // ref count = 1, weak count = 1
            weak_ptr<Test> wptr1 = wptr;        // ref count = 1, weak count = 2

            // Assigning a weak pointer to another weak pointer increases the weak reference count.

            // to get a shred pointer from weak pointer we could use lock().
            shared_ptr<Test> sptr( new Test );  // ref count = 1
            weak_ptr<Test> wptr( sptr );        // ref count = 1, weak count = 1
            weak_ptr<Test> wptr1 = wptr.lock();        // ref count = 1, weak count = 1
        }

###
![alt text](https://www.codeproject.com/KB/cpp/541067/CyclicRef_WP.png "example overview")


###
#boost::asio
some quick notes bout bost asio, so i hade a basic asio progarm and it took me 100 hours to figure out which files i need to link in order to compile (found stack overflow post - thanks to the answerer) and these are the three files u need to link in order to use boost::asio, can't they put it in their docs, fuckk!
        
        c++ -I /path/to/boost_1_67_0 example.cpp -o example -lpthread -lboost_system -lboost_signals ( -lboost_thread -  if u are using thread.)

####
asio simple print nums a second programmed borrowed from ( boost.org ) ***please refer to boost.org/doc/boost_asio/tutorial for explaination***


    #include <iostream>
    #include <boost/asio.hpp>
    #include <boost/bind.hpp>
    #include <boost/date_time/posix_time/posix_time.hpp>

    class Printer {
        public: 
            Printer(boost::asio::io_context& io) : timer_(io, boost::posix_time::seconds(1)), count_(0) 
            {   
                /* 
                   since every non-static member function has implicit `this` we need to bind `this` parameter 
                   boost::bind() converts a callback handler ( in this case memeber fucntion ) into a function
                   member that can be invoked as tho it has the signature void(const bost::system::error_code&)

                */
                timer_.async_wait(boost::bind(&Printer::print, this));
            }

            ~Printer() {
                std::cout << "Final Count: " << count_ << '\n';
            }

            void print() {
                if (count_ < 5) {
                    std::cout << count_ << '\n';
                    ++count_;

                    timer_.expires_at(timer_.expires_at() + boost::posix_time::seconds(1));
                    timer_.async_wait(boost::bind(&Printer::print, this));
                }
            }

            private:
                boost::asio::deadline_timer timer_;
                int count_;

    };

    int main() {

        //all programs that use asio have to have at least one `context` object
        boost::asio::io_context io;
        Printer p(io);

        io.run();

        
        return 0;
    }


####

simple asio program to demonstrate async handling w/ strand in multithreaded programs

    #include <iostream>
    #include <boost/asio.hpp>
    #include <boost/bind.hpp>
    #include <boost/thread/thread.hpp>
    #include <boost/date_time/posix_time/posix_time.hpp>

    class Printer {
        public:
            Printer(boost::asio::io_context& io) :
                _strand(io), _timer1(io, boost::posix_time::seconds(1)),
                _count(0),   _timer2(io, boost::posix_time::seconds(1))
            {
                _timer1.async_wait(boost::asio::bind_executor(_strand, boost::bind(&Printer::print1, this)));
                _timer2.async_wait(boost::asio::bind_executor(_strand, boost::bind(&Printer::print2, this)));
            }

            void print1() {
                if (_count < 10) {
                    std::cout << "Timer 1: " << _count << '\n';
                    ++_count;

                    _timer1.expires_at(_timer1.expires_at() + boost::posix_time::seconds(1));
                    _timer1.async_wait(boost::asio::bind_executor(_strand, boost::bind(&Printer::print1, this)));
                    
                } else {
                    this->~Printer();
                }
            } 

            void print2() {
                if (_count < 10) {
                    std::cout << "Timer 2: " << _count << '\n';
                    ++_count;

                    _timer2.expires_at(_timer2.expires_at() + boost::posix_time::seconds(1));
                    _timer2.async_wait(boost::asio::bind_executor(_strand, boost::bind(&Printer::print2, this)));
                    
                } else {
                    exit(1);
                }
            } 

            ~Printer() {
                std::cout << "Final Count: " << _count << '\n';
            }

            private:
                boost::asio::io_context::strand _strand;
                boost::asio::deadline_timer _timer1;
                boost::asio::deadline_timer _timer2;
                int _count;
    };

    int main() {

        //all programs that use asio have to have at least one `context` object
        boost::asio::io_context io;
        Printer p(io);

        boost::thread t(boost::bind(&boost::asio::io_context::run, &io));

        io.run();
        t.join();

        return 0;
    }