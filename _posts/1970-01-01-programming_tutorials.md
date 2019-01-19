---
layout: post
title: "programming tutorials new"
date: 1970-01-01
---




===== Template ======


Function templates do not support default arguements in typelist. The default aurgments appear in the function arguements.
Class templates can take default arguements in type list.


You would generally not use default specification for non-type integer parameter, unless you are utilizing templates for advanced stuff, like meta-programming, static-asserts, SFINAE etc, which definitely demands a separate part. More often you would see and implement default parameters for class templates, which are data-types. An example:

template<class T = int>
class Array100

Array100<float> FloatArray;
Array100<> IntArray; - default paramater.

The template should be well formed.
the dependant type should be explicitly marked with the keyword typename. For non depenadant type, the keyword is optional.Essentially, the compiler would have to compile the template code in two phases: Once for basic syntax checks; and later for each instantiation of function template - where it would perform actual code compilation against the template data-types.

Templates are of two types:

    Function Templates
    Class Templates 

    template<class TYPE>
    void PrintTwice(TYPE data)
    {
        cout<<"Twice: " << data * 2 << endl;
    }

    --------------------------

    class Item
    {
        int Data;
    public:
        Item() : Data(0)
        {}

        void SetData(int nValue)
        { 
            Data = nValue;
        }

        int GetData() const
        {
            return Data;
        }

        void PrintData()
        {
            cout << Data;
        }
    };

Implicit instatiation of template
Explicit instatiation of template
Why would you need explicit type specification? Well, there are multiple reasons:

    You want only specific type to be passed, and not let the compiler intelligently deduce one or more template argument types solely by the actual arguments (function parameters). 

Undoubtedly notice and understand that I have passed explicit specification only for first template parameter, the second type is deduced from second argument of function call.

    When function-template takes template-type, but not from its function arguments. 

Its impossible to deduce type in the below example by the compiler until. Hence the only way is to do an explicit instatiation.
template<class T>
void PrintSize()
{
   cout << "Size of this type:" << sizeof(T);
}

Function templates are templates whereas template functions are instatiation of the templates. The template functions are not the same as a normal written function because a template funciton is genearted by a compiler and a normal function is written by the user.
The difference is

Important! There is a difference between function template and template function.

A function template is body of a function that is bracketed around template keyword, which is not an actual function, and will not be fully compiled by compiler, and is not accountable by the linker. At least one call, for particular data-type(s) is needed to instantiate it, and be put into accountability of compiler and linker. Therefore, the instance of function template Show is instantiated as Show(int) or Show(double).

A template function? Simply put, an "instance of a function template", which is produced when you call it, or cause it to get instantiated for particular data type. The instance of function-template is actually a valid function.

An instance of a function template (aka template-function) is not a normal function, under the umbrella of name-decoration system of compiler and linker. That means, an instance of function-template:

function template
template<class T> 
void Show(T data) { }

normal function
void Show(double data){}

tmeplate function
void Show<double>(double x){}


  Default Arguments with Function Templates
  template<class T>
void PrintNumbers(T array[], int array_size, T filter = T(60))


Class templates - 

Unlike function template instantiation, where arguments of function itself helps the compiler to deduce template type arguments, with class templates you must explicitly pass template type (in angle brackets). 


const - he ending const specifies that you will not modify any member variables of the class the function belongs to. Since there is no class where this function belongs to, you get an error. cv qualifier.

Alright, we have seen that class templates, just like function templates, can take multiple type arguments. But class templates also allow few non-type template arguments. In this part, I will elaborate only one non-type: integer.

In this class template declaration, int SIZE is a non-type argument, which is an integer.

    Only integral data-types can be non-type integer argument, it includes int, char, long, long long, unsigned variants and enums. Types such as float and double are not allowed.
    When being instantiated, only compile time constant integer can be passed. This means 100, 100+99, 1<<3 etc are allowed, since they are compiled time constant expressions. Arguments, that involve function call, like abs(-120), are not allowed.
    As a template argument, floats/doubles etc may be allowed, if they can be converted to integer. 


Class Template -> Template Class -> Object


n that sub-section, the default-argument referred to arguments of function parameters itself, not the type-arguments of function template. Function templates, anyway, do not support default arguments for template-arguments. As a side note, please know that methods of a class template can take default arguments, as any ordinary function/method would take.

Class templates, on other hand, do support default-argument for the type/non-type arguments for the template parameters. Throwing you an example:



====== Random ======


Before C++11, the only way to generate random numbers was to use the C-style srand() and rand() functions. The srand() function needed to be called once in your application and was used to initialize the random number generator, also called seeding.
Once the generator is initialized, random numbers could be generated with rand(). 

A random number engine is responsible for generating the actual random numbers and storing the state for generating subsequent random numbers. The distribution determines the range of the generated random numbers and how they are mathematically distributed within that range. A random number engine adaptor modifies the results of a random number engine you associate it with.

Engines:

  The classic Minimum Standard rand0 of Lewis, Goodman, and Miller.  This is cheap to run and low cost. More professional are mentioned below.
  default random engine is linear congurential engine0.

  random device engine - based on a real hardware such as radioative isotope by counting alpha particles per time interval or the noise in reverse biased diode.

  The below are pseudo random engine.
  An alternative LCR (Lehmer Generator function). linear congurential engine
  The state is a single integer containing the last generated random number or the initial seed if no random number has been generated yet.

  mersenne twister engine

  subtract_with_carry_engine

The quality of the random number generator is referred to as its entropy measures.
The entropy() method of the random_device class returns 0.0 if it is using a software-based pseudo-random number generator, and returns a nonzero value if there is a hardware device attached. The nonzero value is an estimate of the entropy of the attached device.

--------------

By default, an engine (except possibly random_device) gives the same sequence each time a program is run. One can change the seed, and then 
even the default random engine produces separate sequence of numbers.
Random device engine always produces sepaarate sequence everytime it is run. The others would genearte the same sequence for identical seed.
To get an unpredicable sequence, use time of the day.

normal distribution also called the bell curve
uniform distribution
bernoulli distribution
exponential distribution
chi squared distribution


random engine - what are the numbers
distribution - how are the numbers arranged

one can create function objects by using bind. In bind, the first arguement is the object to be called and the second arguement is the argument to the object itself. Example is with uniform or normal distribution with an argument of an engine. 
val = Distribution(engine)


====== Floating point ======

1 singned bit, 8 bit exponent, 23 bit mantissa
1 + 8 + 23 = 32 bits

Calculatin is hence - signed bit * 2 ^ exponent * mantisssa 
Mantissa is always between 1 and 2. When mantissa is 0 then it means 1, when mantissa is 2 it means 2^23. Hence
1 is divided into 2^23 parts and thats also the resolution.

real Exponent is calculated by subrracting 127 from hex exponent.
val = exponent - 127
So, for 2^0, we need to have eponent as 0 and hence exponent as 7F ( 127 ).
So, if the MSB ist set to 1 it means the value is 128. Subtract 128-127 = 1. Hence expoenent is 

If expoenent = 128, then val = 128-127 = 1
Hence the value is 2^1 = 2

Exponent = 0 means val = 0 - 127.
Hence its 0 -127 = -127

The value is hence 2^-127 which is equivalent to 0

The leading invisible bit ( bit 23 ) bit in mantissa is ignored when the exponent is all 0.



====== OpenCV ======


Chapter 1-4

basic type
helper object
large array types

Basic type
fixed vector class
fixed matrix class
point class, scalar class
size class

rectangle class, rotated rectangle classs

the point class and scalar classs can be type casted to vector classes and enjoy the member functions.
size class is restrictive and cannot be typecasted to vector class.

The fixed matrix class can be either instantiated by  cv::Matx33f or cv::Matx<3,3,float>
cv::Matx33f::randu(min, max)
cv::Matx33f::nrandn(mean, variance)

m1.mul(m2) means per element multiplication.
m1 * m2 means matrix multiplication
m1.dot(m2) - sum of element wise multiplicatoin

Many member functions in fixed matrix class is static.

Fixed vector classes are derived from fixed matrix classes, whose column is equal to 1.
This class additionally has cross product that would not make sense for a fixed matrix class. Member access is directly
by () or [] operator unlike large array types where member access needs to be templated.

Complex Class . memeber functions are accessed by re and im unlike STL where member functions are accessed by real() and imag()

Helper Objects:

CV_Assert, CV_DbgAssert(), 
CV_Error(errorcode, description)
CV_Error_(errorcode, sprintf like description)

cv::TermCriteria - EPS or COUNT
cv::Ptr - makePtr ( just like STL unique_ptr or shared_ptr)
cv::Range class
cv::DataType<> template

value_type = float, fmt single character is f, cv::DataDepth<float>::fmt resolves to f, cv::DataDepth<float>::value resolves to the constant CV_32F. The entry channel is 1 because float is just a single number. The last entry in the enum is type which is similiar to depth, but includes the number of channels ( in this case, one ). CV_MAKETYPE(CV_32F,1) resolves to CV_32FC1.

CV_32F is depth and number of channels is 1. Together they make a type constant. Basically 32F is just verbose because F is implicitly 32 bits. so the depth is 32 bits and number of channel is 1.

cv::InputArray and cv::OutputArray casses. cv::InputOutputArray is in-place computation. Any basic type such as cv::Vec, cv::Point, cv::Scalar and cv::Matx in addition to large array types such as cv::Mat and cv::SparseMat is a type of InputArray, OutputArray and InputOutputArray. A kind of void array is cv::noArray() that returns a cv::InputArray() to indicate that this input is not being used.


Utitlity Function - efficiently handle mathematical operations, tests, error generations, memory and thread handling, optimization.

For formatting error messages for exceptions, cv::format() is handy.

large Array Types

  Single channel n dim array padding will always be at the end of of the array whereas multichannel array padding will always be at the end of each row. The memory layout in data is described the array step[]. step[0] contains the pointer to the row and step[1] contains the pointer to each element in the array. This way, step[0]*rows means that multiple rows will be skipped. In a 3 dimensional step[0] would be a plane, that means mulltiple planes would be skipped. 


m.create()
m.setTo(cv::Scalar(a,b,c))

The cv::Mat object is really a header for a data reas, which in principle is an entirely separate thing. For example, it is possible to assign one matrix to another ( m = n ). The data pointed by m would be deallocated and at the same time the refernce couter for the data area that both m an share will be incremented. Last, but not the least, the members of m that chracterize the data such as ros, cols and flags will be pdated to accreatly describe the data now pointed to by data in m. 
It is also possible to point the matrix to a data chunk that alredy exists. 

cv::Mat ( row, col, type, data, step )

ROI - cv::Mat( m, cv::range rows, cv::range cols) or cv::Mat(m,cv::Rect roi)
STL - cv::Mat(const std::vector<>, bool copyData=true)

To access the data, one can also extract a C style pointer to a specific tow of the array. This is done with the ptr<>() template member function of cv::Mat. Recall that the data in the array is contigous by row, thus accessing a specific column using this method would not make any sense )
m.ptr<float>(10) means 10th row of the matrix data m filled with floats.
Another possiblity is the MatIterator to access the data. 

In total, we have three methods - m.at<>(), m.ptr<>() and using m.begin<>(). The iterator automatially handles the padding, that with ptr<>() needs to be first queiried using isContinous()


rng.fill(mat, cv::RNG::UNIFORM, 0.f, 1.f) - fills the mat with random values between 0 and 1

Extracting submatrix - either using member functions such as rowRange() or with () operator by passing a cv::Range or cv::Rect.

The result of the computation ( m0+m1 ) is finally placed in the destination array by operator=(). The result of the expression is dynamically stored in a temporary array and the pointer to this tempporary array is assigned to left hand side. Since the reference count to this temporary array is not 0, hence it is not deallocated.


Chapter 15
Background Subtraction:
In order to perform background subtraction, we first must learn a model of the background. Once learned the model is compared agains the current image and then the known background parts are subtracted away. Static objects or periodically moving objects is a part of background. If we want to make a model of periodically moving objects and static objects of a supermarket parking lot, then it needs to consider the opening hours of the supermarket plus slow moving objects etc. 
To be able to find moving objects against this background, simply subtract the background ( that we just modelled ).


Comparing quick background method against the code book background method. In order to take surrounding pixels into account, we could learn a multipart model, a simple example of which would be an extension of our basic independent  pixel model ( independent because, it assumes that the other pixels do not affect the model ) to include a rudimentary sense of the brightness of neighbouring pixels. The surrounding pixels can be dim or birght. This is a two state model and ofcourse needs more memory and computation power. More general approach would be to have a histogram with all kinds of intensities and make it yet more complex make taking few time steps and not only one frame. cv::erode, dilate and floodFill eliminate any stray patches of pixels.

In my model, I evaluate the flow of the pixels by quantified lambertian surface; hiding corners. the evaluation criteria are the different distances. False positives are those pixels where a movement was detected, but actually no movement was there. 

So, that is another criteria to find out the false positives and false negatives.

The false negatives occur mostly due to textureless areas. 







====== Mathematics ======

Orthonormal basis -

Any three vectors. Choose any two. Find the perpendicular to the projection. This is the second axis. Then find the perpendicular to the projection of projection. This is the third axis.
For any three vectors, this way, orthonormal basis can be made.



<code>


my_unicode = u"Hi \u2119\u01b4\u2602\u210c\xf8\u1f24"

Hi ℙƴ☂ℌøἤ

</code>

====== Python Distutils ======



setup distutils
Setup.py
from distutils.core import setup

setup(name="pynmea",
      version="0.3.0",
      description="Python NMEA Library",
      author="Becky Lewis",
      author_email=" pynmea@scaryclam.co.uk ",
      url=" https://code.google.com/p/pynmea/ ",
      license="MIT",
      packages=['pynmea'])


_init__.py

_VERSION__ =  (0, 3, 0)
def get_version():
    return '.'.join([str(x) for x in __VERSION__])



                                                                              
                                                                              
====== Socket Programming ======

A Client
Socket (), Connect (), Write(), Read()

A Server
Socket(), Bind(), Listen(), Accept(), Read(), Write(), Close()





====== Bootstrapping ======


 is a term used in computer science to describe the techniques involved in writing a compiler (or assembler) in the target programming language which it is intended to compile.

One may then wonder how the chicken and egg problem of creating the compiler was solved: if one needs a compiler for language X to obtain a compiler for language X, how did the first compiler get written? Possible methods include:

    * implementing an interpreter or compiler for language X in language Y.
    * another interpreter or compiler for X has already been written in another language Y; this is how Scheme is often bootstrapped.
    * earlier versions of the compiler were written in a subset of X for which there existed some other compiler; this is how some supersets of Java are bootstrapped.
    * the compiler for X is cross compiled from another architecture where there exists a compiler for X; this is how compilers for C are usually ported to other platforms
    * writing the compiler in X; then hand-compiling it from source (most likely in a non-optimized way) and running that on the code to get an optimized compiler

Methods for distributing compilers in source code include providing a portable bytecode version of the compiler, so as to bootstrap the process of compiling the compiler with itself.

The first language to provide such a bootstrap was NELIAC. The first commercial language to do so was PL/I. Today, a large proportion of programming languages are bootstrapped, including C, Haskell, Scheme, OCaml, Pascal, Modula-2, Oberon, Factor and more.


technique in writing a a compiler....

one need s a compiler for language X to obtain a compiler for language X
inter / compiler for X has already been writtein in language Y..... i make a compiler using language Y, and make a compiler for language X
compiler for X is cross compiled from another architecture

\Phew !!!! cant understand these fuzzy statemnts.

Note that all of the code and data that follows goes into the .text section. It is also in ARM 32-bit code (not Thumb).
One label is made global, _startup. This will be available to other modules in the project and will also appear in the map.
The GNU assembler doesn’t require you .extern anything. If a symbol is not defined in the assembler file, it is automatically assumed to be external.
The vector table is 32 bytes long and is required to be placed at address 0x000000.
You will see later in this tutorial that the interrupt service routines referenced in the Vector Table are just endless-loop stubs in the main.c function and the interrupts are turned off.
The NOP instruction at address 14 is an empty spot to hold the checksum.



Now let us know about the working procedure of flash programming. Firstly, we configure the registers to initialize the system. If the system can work well, we can access RAM and FLASH. Then we will test SDRAM that is "write xxxxxx to mem xxxxxxx, read xxxxx". If we can write and read the SDRAM correctly, then test successfully. If we did not configure the registers correctly, this step will fail.                                       
We suggest our customers setting little endian mode. We test many flashes with this endian mode. About the CPU memory mapping, I think you can configure re-mapping register. You can also refer to the user guide (4.3 CPU Sub-Dialogue). When you configure the register. The following four steps are helpful:                                           
1. Configure the basic registers such as system control register, clock control register that ensure the operation of the system.

2. Disable the watchdog.

3. Configure the relevant registers of the memory area, including Flash chip selected register, which determines the start address of Flash; SARM/DRAM chip selected register, which determines the start address of RAM; DRAM dynamic refreshable register and re-mapping register.

4. Clear all the pending interrupts.


  
http://www.gnu.org/software/binutils/manual/ld-2.9.1/html_chapter/ld_3.html

objcopy -O binary - creates a bin file
objdump -c -h -s    -> creates a listing file the way the target looks like
objcopy -g  -> create a stripped version to load into the traffic
arm-elf-size  -> size -A  file.elf
arm-linux-strip

type conversions

0xc12858a5
0xc0250b14a90470a8
both are -10.521642


====== C Language ======


stidio.h standard input output
ctypes.h - character
math.h
stdlib.h - Utlitliy
assert.h - diagnostics
stdarg.h - variable argument list
setjmp.h - non local jump
signal.h - signal
time.h - date and time fn.
limit.h/float.h

static and extern are called storage class specifiers.

extern says the variable, or function, is defined ouside this source file.

static says the variable, or function, defined in this file can be used only in this file.

static and extern are storage classes. Storage classs indicate duration and scope of the variable. Duration indicates the life span of variable, and scope indicates the visibility of the variable.

Static Storage class - scope is local to the function or the file.

The extern storage class is used to declare a global variable that will be known to the functions in a file and capable of being known to all functions in a program. This storage class has a duration that is permanent. Any var             iable of this class retains its value until changed by another assignment. The scope is global. A variable can be known or seen by all functions within a program.



A variable or function declared static is said to have internal linkage. Whereas, a variable or function declared extern is said to have external linkage.

There are defaults. Global variables are extern by default. Functions are extern by default. constants are static by default. These defaults can be changed. That is, you can have a static global variable or an extern constant.

If you use the extern explicitly with a global variable you need to assign a value where the variable is defined and no value where the variable is declared.

Code: ( text )

   1.
      const int data = 10;              //has internal linkage
   2.
      extern const int data = 10;    //has external linkage
   3.
      extern const int data;           //const int data defined outside this file
   4.
      extern int data;                    //data defined outside this file
   5.
      extern int data = 10;            //data defined here with a value of 10 and
   6.
                                               //external linkage
   7.
      int data = 10;                      //same as extern int data = 10;
   8.
      static int data = 10;             //has internal linkage


----


token concatenation :

##_
##
##' is probably illegal anywhere outside a comment, string or character literal, or a macro definition.


     struct command
     {
       char *name;
       void (*function) (void);
     };
    
     struct command commands[] =
     {
       { "quit", quit_command },
       { "help", help_command },
       ...
     };

It would be cleaner not to have to give each command name twice, once in the string constant and once in the function name. A macro which takes the name of a command as an argument can make this unnecessary. The string constant can be created with stringification, and the function name by concatenating the argument with `_command'. Here is how it is done:

     #define COMMAND(NAME)  { #NAME, NAME ## _command }
    
     struct command commands[] =
     {
       COMMAND (quit),
       COMMAND (help),
       ...
     };


The second type of user defined datatype is enumerated data type which is defined as follows.

Enum identifier {value1, value2 …. Value n};

The identifier is a user defined enumerated datatype which can be used to declare variables that have one of the values enclosed within the braces. After the definition we can declare variables to be of this ‘new’ type as below.

enum identifier V1, V2, V3, ……… Vn

The enumerated variables V1, V2, ….. Vn can have only one of the values value1, value2 ….. value n

Example:

enum day {Monday, Tuesday, …. Sunday};
enum day week_st, week end;
week_st = Monday;
week_end = Friday;
if(wk_st == Tuesday)
week_en = Saturday;
  

/** brief


==== OpenCV ====

Stereo Global Matching
Graph Cut


Evaluation analysis of tracking

MOTA  higher  100 %   Multiple Object Tracking Accuracy [1]. This measure combines three error sources: false positives, missed targets and identity switches.
MOTP  higher  100 %   Multiple Object Tracking Precision [1]. The misalignment between the annotated and the predicted bounding boxes.
IDF1  higher  100 %   ID F1 Score [2]. The ratio of correctly identified detections over the average number of ground-truth and computed detections.
FAF   lower   0       The average number of false alarms per frame.
MT  higher  100 %     Mostly tracked targets. The ratio of ground-truth trajectories that are covered by a track hypothesis for at least 80% of their respective life span.
ML  lower   0 %     Mostly lost targets. The ratio of ground-truth trajectories that are covered by a track hypothesis for at most 20% of their respective life span.
FP  lower   0       The total number of false positives.
FN  lower   0       The total number of false negatives (missed targets).
ID Sw.  lower   0   The total number of identity switches. Please note that we follow the stricter definition of identity switches as described in [3].
Frag  lower   0     The total number of times a trajectory is fragmented (i.e. interrupted during tracking).
Hz  higher  Inf.    Processing speed (in frames per second excluding the detector) on the benchmark.
MOTA - Multiple Object Tracking Analysis


Benchmark Statistics
Sequences Frames  Trajectories  Boxes
11  5783  721 61440


Difficulty Analysis

Sequence difficulty (from easiest to hardest, measured by average MOTA)
100 % easy . lesser is difficult 


In LK, if the next points are not found, then the feautures should be calculated again. This happens when two images in a sequence are identical. The points are hence removed because LK forgets these points. Another solution is to remember those points from the last image.

Homography means same word but dfferent phonetics. Hence viking can be either said veiking or viking.
This is the same with pcitures. A picture can be recitified on edges, distorted, but the picture itself does not change.
A homography matrix is calclulated that contains the rotational and translational vectors. The homography matrix in internal to the 
camera sensors and the build. It is done primarily during the calibraion process. Once the parameters are recealed, 
rotation and translation can be mapped to the original image, if the homography matrix is known.

 Mat ( row, column )
 Size ( width, height ) which is equivalent to ( column, row )

 create a directory release and then invoke
 cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=../build ..
 It is important to build with gtk support, otherwise, the opencv will built, but the programs wont show any images
 for example cvNamedWindow wont work.

 Motion Sensing Applications ( Optical Flow )

 Kinetic Sensors: 1 Monochrome CMOS Receptor ( in short a camera lens ),
 1 Infrared Camera to monitor depth and
 1 Microphone array.
 Additionally 3 axis accelerometers to find out if the kinetic is placed on a shelf which is
 tilted. The angle would be then compensated in the software.

 These sensors have a narrow imaging area of about 58 degrees horizontal and 43 degrees vertical. It can also not
 detect anything within the first 0.5 meters (~20 inches). Highly reflective surfaces, such as metals, glass, or
 mirrors cannot be detected by the 3D vision sensor.


 Depth cloud: Depth cloud is another name for the depth_image produced by the 3D sensor, such as the Kinect, ASUS,
 and PrimeSense depth cameras.
 Point cloud: A point cloud is a set of points with x, y, and z coordinates that represent the surface of an object.
 Registered DepthCloud and Registered PointCloud: These terms are used by ROS for special DepthCloud or PointCloud
 data colored by the rgb image data. These data streams are available when the depth_registration option is selected
 (set to true).

 Without BUILD_FFMPEG flag

 --   Checking for modules 'libavcodec;libavformat;libavutil;libswscale'
 --   Found libavcodec, version 56.60.100
 --   Found libavformat, version 56.40.101
 --   Found libavutil, version 54.31.100
 --   Found libswscale, version 3.1.101

 sudo apt-get install python-opencv

 -Wl,Blsymbolic ; --enable-pic ; --disable-static

 --------------------------------------------------------------------------------

 HighGUI - Functions, that allow to interact with the operating system, the file system and the the hardware such as
 cameras.
 - read and write graphics-related files
 - handle mouse and keyboard events
 - create sliders etc.
 - much of the code is redundant, because QT does it better.
 - still and video images.
 - provides a set of XML/YAML based functions for human readable, text based format.



 cv::cvtColor() - convert from one color space to another and also specify the number of destination channels.
 cv::mixChannels() - mix channels from one array to another

 cv::abs - element by element absolute of the matrix
 cv::absdiff() - element by element subtraction and saturation between two matrices
 cv::add() - elment by element addition and saturation between two matrices
 cv::addWeighted() - element by element weight (alpha,beta) mult and offset (gamma) addition between two matrices.
 cv::exp() - element by element exponential
 cv::convertScaleAbs() - scale, offset, absolut and saturate on single matrix.
 cv::log() - natural log element by element. For negative or zero, the destination element is a large neg value.
 cv::divide() - divide element by element matrix with a scalar or matrix and a matrix.
 cv::multiply() - multiply element by element btw. two matrix. scaling and saturation is also done.
 cv::eigen - calculautes all or few largest eigen value and eigen vector for a symmetric matrix with floating data pt.
 cv::bitwise_and(), cv::bitwise:or(), c::bitweise:not(), cv::bitwise_or(), cv::bitwise_xor() - element by element.
 cv::pow() - src^pow

 cv::calcCovarMatrix() - mean and covariance matrix of the 1 by n or n by 1 samples.
 cv::mean() - mean of all the value including the channels. the computation is done only on non masked elements.
 cv::meanStdDev() - mean and standard deviation of all the value including the channels.
 cv::Mahalanobis() - Calculates inverse covariance ( distance ) from a point x and the distributions mean.
 cv:cartToPolar() - two input arrays, each consists of x and the other consists of y component. Result is mag and angle.
 cv::magnitude() - two input arrays, each consists of x and the other consists of y component. Result is mag.
 cv::phase() - like magnitude, Result is angle
 cv::determinant() - determinant of a square matrix with floating data pt. and 1 channel. Large with Gaussian elimin.
 cv::mulTransposed() - multiple with transpose, optionally subtract delta and also scale.
 cv::polarToCart()

 cv::completeSymm() - copy the lower triangle to the upper or vice versa. Makes matrix symm. Diag remains unchanged.
 cv::flip() - flip around x axis or y axis or both
 cv::invert() - inverts a square matrix, but may be non square if pseudo inverse. Uses Gauss elim, SVD, and Cholesky.

 cv::countNonZero() - counts the number of nonzero pixels in the matrix.
 cv::compare() - element by element comparison and either 255 or 0, if the matrix elements ( =, >, <, <=, >=, != )
 cv::inRange() - Only for 1 D multi channel, element <, > lower and upper, then 255 otherwise 0.
 cv::checkRange() - returns true or false or exception if any element in the array is out of minVal or maxVal.
 cv::max(), cv::min()  - computes the max / min between two matrices.
 cv::merge() - merge different cv::Mat in one. The inputs are a array of std::vector<cv::Mat>
 cv::minMaxIdx() - for 1D, eturns minVal, maxVal and their corresponding indexes
 cv::minMaxLoc() - for 2D, returns minVal, maxVal and their corresponding cv::Points.

 cv::randu() - create random array from min number and max number. Uniformly distributed random values.
 Generated by Multiply with Carry Algorithm.
 cv::randn() - create random array from mean and standard deviation. Normally distributed random values.
 Gaussian-distribution random numbers are generated using Ziggurat algorithm.
 cv::randShuffle() - shuffles a 1D array.

 cv::solvePoly() : solve univariate polynomials
 cv::solve() : linear equation and least square problems ( uses SVD pr QR).
 cv::cubic() :
 cv::solveLP : linear programming problem using the Simplex Algorithm (Simplex Method).

 cv::imread() - reads an image, GRAY, BGR, BGRA etc.
     The first few bytes of the file ( signature or magic sequence ) determines the codec.
     All of them load 8 bits, except ANYDEPTH. Only if WITH_JPEG=ON, otherwise no jpeg extension can be read.
     cv::IMREAD_COLOR 	    Always load to three-channel array. 	default
     cv::IMREAD_GRAYSCALE 	Always load to single-channel array.
     cv::IMREAD_ANYCOLOR 	Channels as indicated by file (up to three).
     cv::IMREAD_ANYDEPTH 	Allow loading of more than 8-bit depth.
     cv::IMREAD_UNCHANGED 	Equivalent to combining: cv::IMREAD_ANYCOLOR | cv::IMREAD_ANYDEPTH
 cv::imwrite() - writes an image, compression algo should be given. jpg, png, tiff, bmp,
    PNG is not lossless. It depends on the compression. 0 is lossless. But the default is 3 and is lossy.
    imwrite will store mostly 8bit per channel, but 16 bit and float format is also allowed. Return value is true or
    false if the image was saved or not.
    cv::IMWRITE_JPG_QUALITY 	JPEG quality 	0–100 	95
    cv::IMWRITE_PNG_COMPRESSION 	PNG compression (higher values mean more compression) 	0-9 	3
    cv::IMWRITE_PXM_BINARY 	Use binary format for PPM, PGM, or PBM files 	0 or 1 	1
 cv::Mat::isempty() - check if its really an image?
 cv::imencode() - compresses / encodes a Mat to vector<uchar> in the memory. No file is written on the filesystem.
 cv::imdecode() - decompresses / decodes a vector<uchar>from the memory to Mat.
    returns an empty array if the buffer it is given is empty or invalid / unusable data.
 cv::VideoCapture() - either -1, filename or device. .mpg, avi. If device, then identifier+domain.
    In case of a file, OpenCV needs to know how the file should be decoded. In case of a device, an identifier (
    which camera should be acccessed, for single camera on the computer, it is 0 ) and a domain needs to be supplied.
    The domain is a predetermined constant, and determines how OpenCV would like to talk to the camera.
    When empty, then open() needs to be called.
 cv::VideoCapture()::isOpened() - check if the video can really be opened?
 cv::VideoCapture()::read()
 cv::VideoCapture& cv::VideoCapture::operator>>
 cv::VideoCapture::grab( void )
 cv::VideoCapture::retrieve()
 cv::VideoCapture::get()
 cv::VideoCapture::set()
    cv::CAP_PROP_POS_MSEC 	  	Current position in video file (milliseconds) or video capture timestamp
    cv::CAP_PROP_POS_FRAMES 	  	Zero-based index of next frame
    cv::CAP_PROP_POS_AVI_RATIO 	  	Relative position in the video (range is 0.0 to 1.0)
    cv::CAP_PROP_FRAME_WIDTH 	  	Width of frames in the video
    cv::CAP_PROP_FRAME_HEIGHT 	  	Height of frames in the video
    cv::CAP_PROP_FPS 	  	Frame rate at which the video was recorded
    cv::CAP_PROP_FOURCC 	  	Four character code indicating codec
    cv::CAP_PROP_FRAME_COUNT 	  	Total number of frames in a video file
    cv::CAP_PROP_FORMAT 	  	Format of the Mat objects returned (e.g., CV_8UC3)
    cv::CAP_PROP_MODE 	  	Indicates capture mode; values are specific to video backend being used (e.g., DC1394)
    cv::CAP_PROP_BRIGHTNESS 	✓ 	Brightness setting for camera (when supported)
    cv::CAP_PROP_CONTRAST 	✓ 	Contrast setting for camera (when supported)
    cv::CAP_PROP_SATURATION 	✓ 	Saturation setting for camera (when supported)
    cv::CAP_PROP_HUE 	✓ 	Hue setting for camera (when supported)
    cv::CAP_PROP_GAIN 	✓ 	Gain setting for camera (when supported)
    cv::CAP_PROP_EXPOSURE 	✓ 	Exposure setting for camera (when supported)
    cv::CAP_PROP_CONVERT_RGB 	✓ 	If nonzero, captured images will be converted to have three channels
    cv::CAP_PROP_WHITE_BALANCE 	✓ 	White balance setting for camera (when supported)
    cv::CAP_PROP_RECTIFICATION 	✓ 	Rectification flag for stereo cameras (DC1394-2.x only)
        cap.get( cv::CAP_PROP_FOURCC );

 cv::VideoWriter::VideoWriter(
    .jpg or .jpeg: baseline JPEG; 8-bit; one- or three-channel input
    .jp2: JPEG 2000; 8-bit or 16-bit; one- or three-channel input
    .tif or .tiff: TIFF; 8- or 16-bit; one-, three-, or four-channel input
    .png: PNG; 8- or 16-bit; one-, three-, or four-channel input
    .bmp: BMP; 8-bit; one-, three-, or four-channel input
    .ppm, .pgm: NetPBM; 8-bit; one-channel (PGM - portable gray map ) or three-channel (PPM - pixmap), (PBM - bitmap) .

 Sometimes, it is important to provide the matrix data as text data and not binary data. This is important for
 example to save calibration values of the camera. Ofcourse, the calibration values could be saved as bin files, but
 then it is not immediate comparable with different calibration files. Hence, OpenCV provides functions to save the
 data in either XML or YAML format. The YAML format comprises of mapping and sequences. Mapping is like a dictionary
 denoted by { and sequence is like a list with a series of numbers. List members are denoted by a leading hyphen (-)
 with one member per line or enclosed in square brackets ([ ]) and separated by comma space (, ). Apart from the
 conventional { and [, there are two more character sequences, {: and [:. They put the subequent lists in the same
 line. The {: and [: is simply ignored in XML formats, because the file layout is pretty constant, however not so
 comfortable to read. YAML wins when readability of the file needs to be maintained. The conversion to XML or YAML
 formats is called serialisation.
 cv::FileStorage::FileStorage( string fileName, int flag );
 cv::FileStorage::open( string fileName, int flag );
 cv::FileStorage::WRITE or cv::FileStorage::APPEND, cv::FileStorage::READ
 cv::FileStorage::release()
 << writes to the file. >> reads from a file

 The return value of this operator is not the desired object, however; it is an object of type cv::FileNode, which
 represents the value that goes with the given key in an abstract form.
 cv::Mat anArray;
 myFileStorage["calibrationMatrix"] >> anArray; // cv::FileNode >> cv::Mat
 cv::FileNodeIterator()
 cv::FileNode::name()
 cv::FileNode::begin() and end() returns a cv::FileNodeIterator that can be used to increment and decrement the
 operator.
 FileNode.begin() returns the FileNodeIterator  and FileNode.end returns the "after last" FileNodeIterator for either
 a mapping or a sequence. Once we have the FileNodeIterator, the FileNode can be obtained by dereferencing the
 FileNodeOperator.  The FileNode can be further dereferenced by either typecasting or redirection operator.
  - first -> this can have many mappings, listings etc and all of them are referenced using their names.
  - second
  - third


 cv::split() - splits into different channels
 cv::accumulate()
 cv::convertTo() - converts an image from one type to another. also see cv::cvtColor()
 cv::threshold() - src > threshold, then do this, otherwise do that.
    cv::THRESH_OTSU by comparing the varaince of pixels above the threshold and below the threshold. The algorithm
    hence sets an optimal threshold values, by searching for all possible thresholds in the space.
 cv::adaptiveThreshold()
 cv::copyMakeBorder() - makes borders based on specific algorithms
 cv::borderInterpolate() - returns the donor pixels that created the border


 cv::dct()
 cv::dft()
 cv::idct()
 cv::idft()
 cv::norm
 cv::normalize()
 cv::perspectiveTransform()
 gemm(), getElementScale...
 cv::mulSpectrum()
 cv::determinant() - single value decomposition.
 cv::GaussianBlur() - convolute the source image with a gaussian kernel with

 Humans see because of our eyes have sensors that is respondent to RGB. This doesnt mean that all creatures have the
 same potential. The bulls, lions, bees, snakes, respond differently to the same object because the sensors in their
 eyes stimulate to a different wavelength.
 RGB colors are additive and hence mixing with each other ( adding their components ) would give a different color.
 The addition is done on a completely black colour.
 CMY colors are subtractive colours. The subtraction is done on a completely white colour.
 In digital cameras, the light is focussed on an image plane. But the problem is that the lenses diffract differently
 for different wavelengths. And hence, some kind of correction needs to be done. The major wavelengths denoted by
 Fraunhofer D ( yellow ), Fraunhofer B ( blue ) and Fraunhofer C ( red ) lines are taken for correction and most of
 the time is enough for a good image. These wavelenths then must focus on a common point, otherwise, chromatic
 abberations will occur. A pair of convex lens and a concave lens makes it possible to focus the above lines onto a
 single plane.

 OpenCV was initially based on C and with OpenCV2.0 has been changed to C++. One of the main reasons are:
 1. Automatic memory allocation and deallocation ( constructors and destructors )
 2. Object oriented containers.
 3. The data pointer remains fixed for the images. Only headers are copied from one object to another.
 The cpmputation directly on the matrix irrespective of the functions saves some resources and computation time.
 There is no need to copy the matrix here and there, because the data is changed inline.
 There is only one single copy of the data, and only the headers are created. So,
     Mat A;
     Mat B(A);
     Mat C; C = A;
     Mat D = A;
  all have one data, but different headers. So the matrix operation on C will directly change the data of A ( but not
  the header ). The assigmnent operator and the copy constructor only copies the header.
  If you really want to copy the data also, then source.clone and source.copyTo(target) must be done.
     Mat F = A.clone();
     A = cv::imread(argv[1], CV_LOAD_IMAGE_COLOR);
  Everytime a new matrix is created and is assigned or copy constructed ( XX reference ), then a reference counting
  mechanism counts the number of objects that the data is being referred to. When the last object is deleted, that is
  referring the real data ( image data ), then the data memory is also deallocated and correspondingly destructed (
  shredded ). Remember delete does not mean that the object is shredded. delete just takes away the life, but does
  not garbage dump the data yet.

  Color Coding:
  BGR is the OpenCV type. Other color codes are RGB, HSV, HSL, YCrCb, CIE L*a*b*
  The data used can be 8 bit signed or unsigned or 32 bit signed or unsigned float or even 64 bit double !!

  imread()
  The function determines the type of an image by the content, not by the file extension.
  In the case of color images, the decoded images will have the channels stored in B G R order.
  OPENCV_BUILD_3RDPARTY_LIBS flag in CMake would let you compile the relevant codecs.

  The image processing is just a game of numbers. It could be that the intensity has suddenly spiked up and this is
  known as a spike or a high frequency. If a statistics is taken to find out the difference in the pixel number from
  the neighbouring pixels, then any pixel which changes to a difference of for example 100 would be considered high
  frequency. These high frequencies are also introduced for example by scaling the images down. The
  downsampling is done by convolving the image with a series of delta functions. This convolution algorithm
  introduces high frequencies in the images, that needs to be filtered out later.

  Converting a RGB to Grayscale is as simple as taking the individual RGB values and averaging them. For example
  simply divide by 3, or there are other algorithms where weighted average is taken and green is given more weight:
  0.21 R + 0.72 G + 0.07 B. Also a max of RGB and min of RGB is added and is then divided by 2.

  cv::Vec3b -> typedef Vec<uchar, 3> Vec3b; -> 1 dimensional array with 3 char elements
  Each index is an array of 3 values i.e its a 2DArray and each element consists of 3 element 1D array.



  Basic Data Type ( cv::Matx<float,T,T>, cv::Vec<float,T>, cv::Size_<T>, cv::Point_<T>, cv::Point3_<T>,
  cv::RotatedRect<point, size, float>, cv::Rect<>

  Fixed Matrix classes:
      are classes whose dimensions are known at compile time. As a result, all memory for their data
      is allocated on the stack, which means that they allocate and clean up quickly. Operations on them are fast and
      there are even more specialized optimized implementations for small matrices.
      Representation: cv::Matx or correspnding aliases.
      Definition: cv::Matx<float,3,3>
      Access: m(3,1)
      Reshape: m.reshape<9,9>()
      Get Row / Column : m.col(1), m.row(1)
      Get diagnoal: m.diag()
      Transpose: m.t()
      Invert: m.inv(method) - default is cv::DECOMP_LU
      Per element mul: m.mul(m2)
      Normal multiplication: m1*m2, m1+m2, m1-m2
      solve linear system: m31f = m33f.solve(rhs31f, method)
      ::eye(), ::ones(), ::zeros(), ::all(x)
      Dotproduct: m1.dot(m2) - Dot product is essentially multiplying the corresponding elements and adding them all. It
      needs to be done on equal dimension matrix. Dot product -> a.b = |a||b|cos(þ),
      It is important to give the type of the object to .at when accessing a Mat object, because Mat can hold any
      kind of type at run time. It is the duty of the programmer to extract the type which he thinks that Mat would
      hold before accessing the elements. This can be made simply by explicitly decalaring Mat with the object type
      already at the declaration. This is done by Mat_. After this the programmer does not need to specify the type
      everytime a member function of Mat_ is accessed, simply because the type is already known to the compiler.

      Fixed Vector classes:
      are derived from the fixed matrix classes and other classes such as cv::Scalar derive from fixed vector classes.
      They are really just convinience functions for Matx. Fixed vector classes is a Fixed matrix class whose number of
      columns is one. Since it is inherited, the fixed vector class inherits everything from fixed matrix class.
      members access: v[i] # Please note the difference in parantheses from member access for single column fixed matrix
      class. m(i).
      Definition: cv::Vec<float,3>
      Access: v(3)
      Cross product: v3f.cross(u3f) - Cross product is always on between two 1 dimensional matrix. Hence this does not
      appear in cv::Matx. It needs to be done on equal dimension matrix. Cross product -> axb = |a||b|sin(þ)


  Helper Object ( cv::Ptr, cv::TermCriteria, cv::Range )

  Helper objects are helpful for controlling various algorithms such as termination criteria or for doing operations
  on the containers such as ranges or slices. There is also one very important object called a smart pointer object
  cv::Ptr.
  Termination criteria take the form of either some finite number of iterations or some kind of error parameters,
  that basically say if one is too close to this number ( epsilon ), then you can quit. The cv::TermCritera can be
  passed to an OpenCV algorithm. The member variables, type, maxCount and epsilon are public. If the termination
  criteria incudes Cv::TermCriteria::COUNT, then you are telling the algorithm to terminate after maxCount iterations.
  If the terminate criterion includes cv::TermCrtieria::EPS, then you are telling the algorithm to terminate after
  some metric associated with the algorithms convergence falls below epsilon.
  cv::Range class is used to specify a continous sequence of integers.
  cv::Ptr is a smart pointer, that allows us to create a reference to something and then pass it around. Everytime a
  reference is created, a reference count is incremented and subsequently decremented when the reference goes out of
  scope. When the reference ( instances of pointer ) count goes to 0, then the Ptr is destroyed.
  The cv::Ptr takes an object that needs to be wrapped. For example:
  cv::Ptr<cv::Matx<float,3,3> > p = makePtr<cv::Matx<float,3,3> >(). The constructor for the template object takes a
  pointer ot the object to be pointed to. This instantiates a smart pointer p, which is a sort of pointer like
  object, that you can pass around and use like a normal pointer ( uses . and -> ).
  addref() and release() increment and decrement the internal reference counter of the pointer. however should not be
  used, cause its the job of the class itself to inrement and dec the reference count.
  empty() determines, if the object still exists where the pointer is pointing to.

  cv::Exception has members
  code : numerical error code
  err : a string indicating the nature of error code that generated the exception
  func : name of the function where the occur occured
  file : the file in which the error occured
  line : the line on which the error occured.
  CV_Error(code, description)
  CV_Error_(code, printf_fmt_str, args)
  CV_Assert(condition) - throws exception if the condition is not met.

  cv::InputArray, cv::OutputArray:
  Any of the cv::Scalar, cv::Vec, cv::Matx, std::vector<>, cv::Mat and cv::SparseMat is defined by cv::InputArray and
  cv::OutputArray. The primary difference between the two is InputArray is const OutputArray is not.
  The InputArray and OutputArray is primarily to keep the interfaces from becoming complicated and reperetive. OpenCV
  defines the types InputArray and OutputArray that takes any of the array types as Input and Output. There is
  another class called InputOutputArray for in-place computation.

  Utility and system functions:
  cv::getTickCount(), cv::getThreadNum() and many more.......... Page 60


  Big Containers / Large Array type:

  Usage Mat:
  - Use the create(nrows, ncols, type) method or the similar Mat(nrows, ncols, type[, fillValue]) constructor.
  - CV_8UC1 means a 8-bit single-channel array, CV_32FC2 means a 2-channel (complex) floating-point array, and so on.
  - Mat M(7,7,CV_32FC2,Scalar(1,3));    // make a 7x7 complex matrix filled with 1+3j.
  - int sz[] = {100, 100, 100};
    Mat bigCube(3, sz, CV_8U, Scalar::all(0)); // create a 100x100x100 8-bit array
 - Use a copy constructor or assignment operator where there can be an array or expression on the right side (see below)
   As noted in the introduction, the array assignment is an O(1) operation because it only copies the header and
   increases the reference counter. The Mat::clone() method can be used to get a full (deep) copy of the array when
   you need it.
     // add the 5-th row, multiplied by 3 to the 3rd row
    M.row(3) = M.row(3) + M.row(5)*3;
    // now copy the 7-th column to the 1-st column
    // M.col(1) = M.col(7); // this will not work
    Mat M1 = M.col(1);
    M.col(7).copyTo(M1);
    // create a new 320x240 image
    Mat img(Size(320,240),CV_8UC3);
    // select a ROI
    Mat roi(img, Rect(10,10,100,100));
    // fill the ROI with (0,255,0) (which is green in RGB space);
    // the original 320x240 image will be modified
    roi = Scalar(0,255,0);
    Due to the additional datastart and dataend members, it is possible to compute a relative sub-array position in the
    main *container* array using locateROI():
    Mat A = Mat::eye(10, 10, CV_32S);
    // extracts A columns, 1 (inclusive) to 3 (exclusive).
    Mat B = A(Range::all(), Range(1, 3));
    // extracts B rows, 5 (inclusive) to 9 (exclusive).
    // that is, C \~ A(Range(5, 9), Range(1, 3))
    Mat C = B(Range(5, 9), Range::all());
    Size size; Point ofs;
    C.locateROI(size, ofs);
    As in case of whole matrices, if you need a deep copy, use the `clone()` method of the extracted sub-matrices.
    - Make a header for user-allocated data. It can be useful to do the following: -# Process "foreign" data using
    OpenCV (for example, when you implement a DirectShow\* filter or a processing module for gstreamer, and so on)
    . For example:
        void process_video_frame(const unsigned char* pixels,
                                 int width, int height, int step)
        {
            Mat img(height, width, CV_8UC3, pixels, step);
            GaussianBlur(img, img, Size(7,7), 1.5, 1.5);
        }
   -  Quickly initialize small matrices and/or get a super-fast element access.
        double m[3][3] = \{\{a, b, c}, {d, e, f}, {g, h, i\}\};
        Mat M = Mat(3, 3, CV_64F, m).inv(); Partial yet very common cases of this *user-allocated data* case are
        conversions from CvMat and IplImage to Mat. For this purpose, there is function cv::cvarrToMat taking pointers
        to CvMat or IplImage and the optional flag indicating whether to copy the data or not. size will be
        (width=10,height=10) and the ofs will be (x=1, y=5)

 Unlike Vec and Matx that are used only for max 3 dimensions, Mat can be used for any number of dimensions. The data
 is stored in an array, what can be thought of as an n-dimensional analog of raster scan order. In 1 D, the data is
 sequential, in 2 D, data is stored in rows, and in 3D, the data is stored in planes, where each plane is filled row
 by row. Unlike many other implementations, where the elements in the matrices are always primitive data, OpenCV Mat
 elements need not be single numbers, but can also be multiple numbers. In fact an n-dim array and an n-1 dimensional
 multichannel array are very similiar objects. So 1 3D array with single channel and 2D array with a multi channel are
 very  similiar.  Its similiar because the memory structure of both of them differ for example, the way padding
 occurs. The multi channel arrays are not completely sequential, as there is padding either after one full row or
 after one full channel. Multi channel arrays can be created by the "type" CV_32FC(7) - this creates a 7 channel for
 each element.
 An array simply by instantiating has no size and no datatype. But can be asked to be allocated with create().
 cv::Mat is a header for data. One can have many headers pointing to the same data.

 There are innumerous constructors:
 Constructors for 2D matrixes:

    row, col, type
    row, col, type, Scalar
    row, col, type, *data, step
    Size, type
    Size, type, Scalar

 The step is one of the way to initialise a matrix. Scalar gives constant values, but with step a pattern can be
 created. So, data can be initialised either by providing a Scalar ( in which the entire arry will be initialised to
 that value ) or by providing a pointer to an appropriate data block.
 Another way is to copy construct from existing arrays or copy construct regions from existing arrays.
 source, range_rows, range_cols

    source, rect
    source, *range

 The basic means to direct access is the member function at<>(). The way the function works, is that you specialize
 the at<>() template to the data that the matrix contains, then access the element using the rows and column locations.

 Worth noting is the cv::DataType<>. This is the arguement type. The type in the cv::Mat constructor can also take
 cv::DataType<cv::Complexf>::type for example.

    cv::Mat tempMatrix(10,10,cv::DataType<float>::type);
    cv::Mat tempMatrix(10,10,cv::DataType<cv::Complexf>::type);
    
    
 Another way is the C Style ptr<>() member function. Unlike at, ptr returns a address. Once the address is there, you
 can manipulate with pointer operations. For example, given a three channel matrix mtx of type float, the
 construction mtx.ptr<Vec<float,3>>(3) would return the pointer to the first floating point channel of the first
 element in row 3 of the matrix.
 
 The third way is to use the member variable data and to use the member array step[] to compute addresses.
 Sometimes, the rows are not continous because of padding. Hence the member function isContinous() returns if its OK
 to iterate the whole array with a pointer.
 
 The last method is to use cv::MatIterator<>. The cv::Mat method begin() and end() return objects of this type. This
 method is smart, because it knows about the continuity and sequential of the array. Example:
 
 A 3D array of size 4*4
    cv::Size sz(10,10);
    cv::Mat m3(3,sz,CV_32FC3);
    cv::randu(m,1,2);:
    cv::MatIterator<cv::Vec<float,3>> it = m.begin();
    for (i = 0; it != m.end(); it++;i++ ) {
        vec.push_back(*it);
    }

 The main idea behing cv::Mat is to separate the header and the workspace. Headers are created instantly, but the
 workspace remains fixed unless a copyTo is performed.

 Filling:
 cv::randu(m,1,2)
 cv::RNG::fill(m,cv::RNG::UNIFORM, 1,2)

 cv::saturate_case<>()

 Statistics:
 eigen values
 eigen vectors
 guassian distribution
 standard deviation : the more spread out the distribution is the greater the standard distribution. A standard
 deviation close to 0 means, that the data points are close to the mean. A higher standard deviation of the same
 mean, would mean that the data points are more spread out.
 Step 1: Add all the numbers and divide by the amount of numbers.
 Step 2: Find the difference between the number and the answer of step 1. Square it.
 Step 3: Add the squared numbers.
 Step 4: Divide by the amount of numbers. Beware that it is sample points - 1.
 Step 5: Square root the answer of step 4. Step 4 is called the Variance of the dataset.

 Correlation: If the correlation between the two numbers is close to 0, that means there is no corrleation at all. If
 it is tending to 1, then when one increases, the other increases too. If it is tending to -1, then when one
 increases, the other decreases. The result of Step 2 and Step 4 is called a z score.
 Step 1: Find the difference between the number and the mean of the first set
 Step 2: Divide the answer in Step 1 by the standard deviation of this set.
 Step 3: Find the difference between the number and the mean of the second set
 Step 4: Divide the answer in Step 3 by the standard deviation of this set.
 Step 5: Multiply the results of Step 2 and Step 4
 Step 6: Repeat this for each sample set and then add all of them.
 Step 7: Divide by the amount of numbers. Beware that it is sample points - 1.

 A linear model  has a correlation of 1 between the x and y points.

That's how you find the standard deviation.
 covariance
 inverse covariance
 determinant
 transpose




  Usage ROI:
    cv::Mat roiRange = img_rgb(cv::Range(100, 300), cv::Range(0, 512)); // start row, end row, start column, end column.
    cv::Mat roiRect = img_rgb(cv::Rect(0,100,512,200)); // start column, start row, width, height

  Point, Vec, Mat, Matx, Scalar, Size, Rect, RotatedRect

  Fixed matrix classes such as Point, Size, Vec, Matx have dimensions that is known at compile time. As a result, all
  memory for their data is allocated on the stack, which means that they allocate and clean up quickly. Operators on
  them are fast, and there are specially optimized implementations for small matrices.


  Scalar:
  Scalar is just for ease of use. As most of OpenCV operates on maximum 4 channel images, so Scalar is a simple class
  which is actually a cv::Vec of length 4, which can be used by OpenCV
  algorithms according to number of channels of the image. Instead of creating an array of different
  length each time, you just pass a scalar value to the algorithm.

  Rectangle and Range:
  If you want to pass both the row and columns, then way is to create a new matrix and pass the source image as the
  first parameter and the section ( range or rectangle ) as the second parameter. This is a kind of a value constructor.


  Summary ( please see Vec and Matx is without underscore )
  Static : Hence the templates consists of dimensions, where the dimensions can vary.
  Point_<T>, Point3_<T>
  Rect_<T>
  Scalar_<T>
  Vec_<T,int>      : dimensions can vary
  Matx<T,int,int>  : dimensions can vary

  Dynamic and hence the template does not consists of dimensions.
  Mat
  Mat_<T>


 Summary
 all(val),
 zero,
 ones,
 eye,
 diag,
 randu(min, max),
 nrandn(mean, variance) : create a matrix with normally distributed entities.

 Access:
 Dynamic
 Mat.at<>()                         : element access ( Mat type defined without template, dynamic dimension )
 Mat.at<cv::Vec>()[]                : channel access ( Mat type defined without template, dynamic dimension)
 Static
 Matx()                             : element access ( Matx type defined with template, static dimension )
 Mat_.at<>() or Mat_()              : element access ( Mat_ type defined with template, static dimension )
 Mat_.at()<cv::Vec>[]  or Mat_()[]  : channel access ( Mat type defined with template, static dimension )

 The purpose of using the template forms Mat_is that you dont have to use the template forms of their member functions.

 Access Subregion: Arrays corresponding to subregions. There is no copy, only headers are defined.
 Data of Mat is not copied to the new arrays unless copyTo() method is used.
 Mat.row()
 Mat.col()
 Mat.rowRange()
 Mat.colRange()
 Mat.rowRange(cv::Range)
 Mat.colRange(cv::Range)
 Mat.diag()
 Mat ( cv::Range, cv::Range )
 Mat ( cv::Rect )


 Ability to create algebraic expressions consisting of matrix arrays and singletons.  The result of the compuation is
 finally placed in the destination array by operator=(). Arrays are semantically referred to be as cv::Mat and matrix
 arrays means something which has a mathematical meaning ie on which matrix operations can be done. A cv::MatExpr is
 assigned to a cv::Mat. m1+m2 is not cv::Mat but a cv::MatExpr. The pointer to the result of MatExpr will be assigned
 to the destination array. The data of the array itself got created temporarily by the MatExpr, but isnt destroyed
 because the scope of the array still exists as the reference is incremented. Apart from simple algebra, there are
 many other operations, one such operation is cv::Mat::eye() or m1*m2 etc etc.. All of these are of the type MatExpr.
 Higher level operations such as transpose and inversions.
 inv(), t(), cross(), dot(), cv::abs(m), cv::norm(m), cv::mean(m), cv::sum(m)

 Underflowing and Overflowing is taken care from cv::saturation_cast<>()
 m0.clone() and m0.copyTo(m1) are the same.

 There are some general rules in OpenCV functions. Ofcourse there are special rules pertaining to individual
 functions, and they are reported by the exceptions. There are some general rules and they apply to all the functions:
 Saturation, Output array, Scalars, Masks, dtype, Inplace operations, Multichannel.

 1. Saturation: Outputs of calculations are saturation-casted to the type of the output array. cv::saturation_case<>()
 uchar& Vxy = m0.at<uchar>(y,x)
 Vxy = cv::saturate_cast<uchar>((Vxy-128)*2 + 128);}
 This explicit saturation_cast truncates the negative value into 0. Otherwise, the answer would have been the 2s
 complement.
 2. Output Array: The output array will be created with cv::Mat::create() if its type and size do not match the
 required type and size. Usually, the required output type and site are the same as inputs, but for some functions,
 xize may be different like for cv::transpose and cv::split
 3. Scalars: Addition of two arrays or an array and a scalar. The result of providing a scalar is the same as if a
 second array had been provided with the same scalar value in every element. Size as described above is taken from
 the input array.
 4: Mask: Whenever the mask argument is present for a function, the output wil be computed only for those elements
 where the value corresponding to the element in the output array is non zero. If the mask arguement is not
 present, then all the values would be calculated, even if its 0*0.
 5. dtype: This forces the output array to be of a specific type. For example, two CV_8UC1 input array will lead to
 the same output type. However, this can be overridden with the dtype=CV_32FC1.
 6. Inplace operation: One can specify the same arrays for both input and output. Its completely legal to do it, but
 ofcourse, it should be clear that the input array will completely loose its data.
 7. Multichannel: Each channel is processed separately, if multichannel arguements are set.



 In electronics and signal processing, a Gaussian filter is a filter whose impulse response is a Gaussian function (
 or an ( or an approximation to it ) . Gaussian filters have the properties of having no overshoot to a step function
 while minimizing the rise and fall time. This behaviour is closely connected to the fact that the Gaussian filter ha
 the minimum possible group delay. It is considered the ideal time domain filter, just as the sinc is the ideal
 frequency domain filter.  Mathematically, a Gaussian filter modfies the input signal by convolution with a Gaussian
 function. What are the different kinds of filters:

 1. Butterworth filter
 2. Chebyshev filter
 3. Elliptic filter
 4. Bessel filter
 5. Gaussian filter
 6. Optimum L ( Legendre ) filter
 7. Linkwitz-Riley filter

 Gaussian Blur:
 Mathematically applying Gaussian blur to an image is the same as convolving the image wih a Guassian function.
 A guassian function is a function of the form -
 Bokeh - a japanese word for blur.

 2i + 3j + 4k ( Unit Vectors )
 We can represent any vector by a linear combination of two vectors. This means the vectors can be spanned anywhere
 in that plane. If the vector has to be represented in another plane, then the linear combination of the two vectors
 wont work, because the span has changed. If two vectors cannot be represented  by scaling one of the vectors, then
 they are said to be linearly independent. An example for linearly independent vectors are the axes. The x axis can
 never be represented by scaling up or down the y axis and vice versa. Linear dependant vectors hence are vectors
 that cannot be represented by a combination of other vectors.
 Dot products are commutative and associative.

 For an arbitrary linear equation, there can be infinite number of solutions, for example, 2x + 4y + 7z + 9w = 1000.
 Hence x,y,z,w can consists of infinite number of solutions.

 The inverse of the matrix A can be calculated by many methods in linear algebra such as Gaussian elimination,
 Eigendecomposition, Cholesky decomposition and Carmer’s rule. A matrix can also be inverted by block inversion
 method and Neuman series. Every matrix can be transposed ( rearranging the columns and rows in a matrix ). The diagonal
 of the matrix remains unchanged. The matrix is symmetric, if the transpose of the matrix is equal to the matrix. Its
 skew symmetric, if the transpose of the matrix is the negative of the original matrix.Ofcourse, for the matrix to be
 symmetric or skew symmetric,  they need to be a square matrix. A(i,j) becomes A(j,i). Complex Conjugate matrix is
 the matrix where the complex number is negated. The real part remains the same.

 Pivot variables, Free variables, Echelon form.
 Imagining 4 vectors defined by 4 equations. The solution of the equation is the point where all the vectors meet
 each other and this point is given by (x1, x2, x3 and x4 )
 A Singular matrix is a matrix whose determinant is 0.

 C++ Libraries to solve linear algebra
 Flint, Singlular, Givaro, Giv ( Scientific Imaging ), Eigen

 Collections
 XML, YAML based functions is more universal in dealing with image coding and decoding.
 The produced YAML (and XML) consists of heterogeneous collections that can be nested. There are 2 types of
 collections: named collections (mappings) and unnamedcollections (sequences). In mappings each element has a name
 and is accessed by name. This is similar to structures and std::map in C/C++ and dictionaries in Python. In
 sequences elements do not have  names, they are accessed by indices. This is similar to arrays and std::vector in
 C/C++ and lists, tuples in Python. “Heterogeneous” means that elements of each single collection can have different
 types.

 Commutative, Associative, Distributive.
 Cross Correlation and Convolution are the same except the kernel is time reversed. Hence cross correlation can be
 implemented efficiently using fast convolution algorithms like overlap-save.
 Overlap-save is an algorithm to evaluate the discrete convolution between a very long signal x [ n ] {\displaystyle
 x[n]}  x[n] and a finite impulse response (FIR) filter h [ n ] {\displaystyle h[n]} h[n]:
 Impulse response is a resonse to an impulse. The impulse response are FIR and IIR. FIR.
 The impulse response defines the response of a linear time-invariant system for all frequencies.
 Linearity means the scaling and adding of individual vectors have the same effect on the output vectors. Time
 invariant, means that a computation at time t will have the same result at time t+T. The only difference will be the
 time delay at the output. Or in other words, time doesnt play a role in the final value of the the computation.
 In other words, convolution in the time domain is equivalent to multiplication in the frequency domain.
 Any LTI system can be characterized entirely by a single function called the systems impulse response. The output
 of the system is simply a convolution of the input to the system with the systems impulse response. So, if we know
 the impulse response of the system through tests, then we can calculate the output of the system for any input
 signal. In the frequency domain, the laplace transform of the impulse response is called the transfer function.
 Impulse is denoted by the term ð ( delta ).

 The Laplace transform of the delta function is 1, so the impulse response is equivalent to the inverse Laplace
 transform of the system's transfer function. In control theory the impulse response is the response of a system to
 a Dirac delta input.

 An FIR filter is designed by finding the coefficients and filter order that meet certain specifications, which can be in the time-domain (e.g. a matched filter) and/or the frequency domain (most common). Matched filters perform a cross-correlation between the input signal and a known pulse-shape. The FIR convolution is a cross-correlation between the input signal and a time-reversed copy of the impulse-response. Therefore, the matched-filter's impulse response is "designed" by sampling the known pulse-shape and using those samples in reverse order as the coefficients of the filter.

 The only differnce between an  IIR and FIR filter is that the IIR filter never settles down to 0. This is because
 the cpaactiros retain a charge indefinetly for an impulse. On the discrete side, which is analogous to FIR filter,
 the memory comes back to its initial state after time t>T.

 For a FIR filter of order N, each value of the output sequence is a weighted sum of the most recent input values.
 The final value is when n has reached N, where beyond N, the value of the output sequence is equal to 0. The above
 compuation is also called discrete convolutoin.

 The convolution of a two dimensional image with a gaussian function can either be done in the spatial domain ( x, y
 ) or the frequency domain. If the convolution is done in the frequency domain, then the concolution is simply an
 inverser fourier transform of the multiplication  ( pixel by pixel ) between the fourier transform of the input
 image and the fourier transform of the gaussian funciton.
 If the spatial domain is used, then the convolution is the double integral of the image multiplied by the gaussian
 function from x and y tending from -infinity to +infinity.

 Convolution as associative, while correlation is not. The associative property is what allows you to convolve multiple filters into a single one, and then convolve that one filter with the image. That is the big advantage of convolution over correlation.

 A crystal can be said as the convolution of the unit cell with the lattice of the crystal. Here the lattice can be
 for example an image, and the unit cell can be thought of as a gaussiann kernel. This way, the gaussian kernel is
 going to be repeated in the entire lattice, forming a perfect crystal.

 Cross coorelation is used to find out the similarity between two different functions. In the convolution theorem,
 the kernel is 180 deg out of phase ( its flipped ) , whereas in cross correlation, there isnt any flip. The cross
 correlation uses the convolution theorem that the fourier of the output is a element by element multiplication of
 the fouriers of the two inputs.
 What is convolution?
 What is convoution theorem?
 What is a PSF?
 What does convolution has to do with the structure of the crystal?
 How might cross correlation be used in crypto FM?

 Auto correlation is between the same signals.


 Algorithms:

 Harris Method - computes derivative operators, analyses them and returns a list of the points that meet our definition.
 Shi and Tomasi method

 Inverse Matrix:
 Sometimes, the calculation needs to be aborted, if the matrix is singular. For example an inverse would make no
 sense for singular matrix. But the calculation is costly and hence, there are methods where a matrix can be
 decomposed into a multiplication of many matrices. One such is LU_DECOMPOSITION. In this algorithm, two matrix is
 decomposed into a lower triangle matrix and a upper triangle matrix. The matrix multiplication of both of them gives
 the original matrix. Its very easy to say if the original matrix is singular, by just multiplying the first element of
 the L with the first element of the upper. If its 0, then the matrix is singular, otherwise not.

 Matrix decomposition methods:
 DECOMP_LU Gaussian elimination with optimal pivot element chosen.
 DECOMP_CHOLESKY Cholesky LL^T factorization; the matrix src1 must be symmetrical and positively defined.
 DECOMP_EIG eigenvalue decomposition; the matrix src1 must be symmetrical.
 DECOMP_SVD singular value decomposition (SVD) method; the system can be over-defined and/or the matrix src1 can be
 singular.
 DECOMP_QR QR factorization; the system can be over-defined and/or the matrix src1 can be singular.
 DECOMP_NORMAL while all the previous flags are mutually exclusive, this flag can be used together with any of the
 previous; it means that the normal equations

 Robust statistics algorithms
 Outlier detection tools

 Matrix:
 Inverse / Reciprocal = fact{Transpose(Adjoint)}{Determinant}
 Orthogonal - Q.t()*Q = I. The inverse of an orthogonal matrix is its transpose.
 Hessenberg - below subdiagonal or above super diagnoal is 0. Important to find eigenvalues.
 Vandermonde Matrix - 1, roots, roots2. The determinant is easily found by products of x_j - x_i

 Eigen Values / Eigen Vectors:
 Companion Matrix -> Characteristicts equation or characteristicts polynomial -> Find roots which is also called
 eigen value -> Find eigen vectors.
 The companion matrix is called companion because its in a sense the companion of polyonomial p.
 In classical linear algebra, the eigenvalues of a matrix are sometimes defined as the roots of the characteristicts
 polynomial. An algorithm to compute the roots of the polynomial by computing the eigenvalues of the corresponding
 companion matrix turns the table on the usual definitions. The eigen value of the companion matrix coincide with the
 roots ( zeros ) of the associated polynomial because, p(z) = det(zI - C_p). M needs to be converted into the
 Hessenberg form.
 QR Algorithm for computing matrix eigen values. QR ( decompose original into orthogonal matrix and the upper
 triangle matrix ).
 Some methods to find the roots of the polynomial are
 Jenkins Traub - rpoly and cpoly
 Companion Matrix

 Linear Least square:
 The linear least square method is most widely solved by QR Decomposition method.


 cv::goodFeaturesToTrack():
    tempted to look for points that have some significant change in them - for example, a strong derivative.





 */







==== GDB =====

breakpoint - execution should stop at a particular location.
watchpoint - execution stops when a particular memory changes value.
catchpoint - execution stops when a particular event occurs.

breakpoint once
breakpoint ignore <number>

GDB has frames that consists of function parameters and local variables. Frame0 is the most innermost frame - the function most recently called.

if else end and other hook commands can be defined using GDB.

GDB can be configured for cross-debugging. Remote targets are usually connected to the host via a serial port or a network connection. 


INT_MIN 


==== REGEX  =====

Negative look ahead


The following paragraph has been taken from - https://www.regular-expressions.info/posix.html and modified to fit my needs

POSIX or "Portable Operating System Interface for uniX" is a collection of standards that define some of the functionality that a (UNIX) operating system should support. One of these standards defines two flavors of regular expressions -

    Basic Regular Expression
    Extended Regular Expression. 

Commands involving regular expressions, such as grep and egrep, implement these flavors on POSIX-compliant UNIX systems. Several database systems also use POSIX regular expressions.

The Basic Regular Expressions or BRE flavor standardizes a flavor similar to the one used by the traditional UNIX grep command. This is pretty much the oldest regular expression flavor still in use today. One thing that sets this flavor apart is that most metacharacters require a backslash to give the metacharacter its flavor. This means, that the metacharacters like ^, $, ( etc can only be used if they are backslashed, otherwise they are literally taken as characters and not metacharacters. Most other flavors, including POSIX ERE, use a backslash to suppress the meaning of metacharacters. On the other hand, in this flavour, backslash on the metacharacter means, that it should ŃOT be taken as metacharacters. Using a backslash to escape a character that is never a metacharacter is an error.

A BRE supports POSIX bracket expressions, which are similar to character classes in other regex flavors, with a few special features. Shorthands are not supported. Other features using the usual metacharacters are the dot to match any character except a line break, the caret and dollar to match the start and end of the string, and the star to repeat the token zero or more times. To match any of these characters literally, escape them with a backslash.

The other BRE metacharacters require a backslash to give them their special meaning. The reason is that the oldest versions of UNIX grep did not support these. The developers of grep wanted to keep it compatible with existing regular expressions, which may use these characters as literal characters. The BRE a{1,2} matches a{1,2} literally, while a\{1,2\} matches a or aa. Some implementations support \? and \+ as an alternative syntax to \{0,1\} and \{1,\}, but \? and \+ are not part of the POSIX standard. Tokens can be grouped with \( and \). Backreferences are the usual \1 through \9. Only up to 9 groups are permitted. E.g. \(ab\)\1 matches abab, while (ab)\1 is invalid since there's no capturing group corresponding to the backreference \1. Use \\1 to match \1 literally.




==== CPP ====

Literature: 

    learncpp.com 
    wikipedia.com
    C++ FAQs - Marshall P Cline
    More Effective C++ - Meyers
    
 * Dynamic data binding - virtual functions. cpp traverses the last overriden function in the derived class.
 * Data encapsulation - interface between the abstraction and the implementation. The data is hidden from the external interface
 * Polymorphism - The base type can be assigned the dervied object type.
 * Inheritance - Code reusability. It implies kind of. Ford is a kind of a car.
 * Composition - It implies part of. Engine is a part of the car. Hence using composition an entire car can be assembled.
 * Data hiding - private and protected data and is only accessible via member funcitons.


    
First ADL and then Template Arguement deduction and then if multiple function calls or function call with different arguements lead to more than one candidate function, then overload resolution is performed to select the function that will actually be called. 
Overloaded functions or overloaded operators.


Arguement dependant lookup ( ADL ) 

Are the set of rules for looking up unqualified function names in function call expressions, including implicit function calls to overloaded operators. These function names are looked up in the namespaces of their arguments in addition to the scopes and namespaces considered by the usual unqualified name lookup.


Methods:
Manager methods: Constructors and Destructors
Accessor methods : Accessing the variables.
Mutator methods: Changing the variables

Access specifier: 

private, public and protected.
public members can be accessed and changed directly from outside.
private members can only be accessed and changed through a public member function or a friend function
protected members can only be accessed and changed through a derived class.

Class and Type:

Different (concrete) classes can produce objects of the same (abstract) type (depending on type system); for example, the type Stack might be implemented with two classes – SmallStack (fast for small stacks, but scales poorly) and ScalableStack (scales well but high overhead for small stacks). Similarly, a given class may have several different constructors.

/**
 Literature:
 Standard Template Library ( Scott Meyers )
 Learncpp.com
 C++ FAQ ( Cline, Molow )
 C++ All-in-One For Dummies, 3rd Edition By: Jeff Cogswell; John Paul Mueller

 A class is a way to abstract behaviour, not just a way to encapsulate bits. A class interface must make
 sense from the outside. If a detached user expects services to access an attribute, those services should exist.
 One should think OO as behaviour centric and not data centric.

 Dynamic data binding - virtual functions. cpp traverses the last overriden function in the derived class.
 Data encapsulation - interface between the abstraction and the implementation. The data is hidden from the external interface
 Polymorphism - The base type can be assigned the dervied object type.
 Inheritance - Code reusability. It implies kind of. Ford is a kind of a car.
 Composition - It implies part of. Engine is a part of the car. Hence using composition an entire car can be assembled.
 Data hiding - private and protected data and is only accessible via member functions.

 ABC ( Abstract Base Class ) are a key to the real world OO design. Often you need an abstraction, where several
 different data structures and algorithms must coexist. In these cases, build an ABC that defines the interface but
 not the implementation and write the user code using the interface defined by the ABC. The compiler prevents the
 creation of objects of the ABC. You can only instantiate a concrete dervied class. Technically, an ABC is a class
 that has one or more pure virtual member functions.

 Pure virtual member function specified that a member function will exist on every object of a concrete derived
 class, even though there is no way to implement this member function in the base class. In other words, it forces
 derived classes to provide a definition for this member function. virtual void draw() const = 0;

 Private members are accessible by members and friends of the class. Protected members are accessible by members and
 friends of the class and also members and friends of the derived class. Public members are accessible by everyone.

 A publicly derived class is a kind of its base class. A pointer to a derived class is in fact pointing to the base
 class.

 The run time system will automatically invoke the proper member function when it has been overridden by a derived
 class ( dynamic binding )

 When a virtual function is invoked, the code that gets called is selected based on the type of the object, rather
 than being selected based on the type of the reference ( this is called dynamic binding, because hte binding
 between the function call and the code to be executed is resolved at run time ). In contrast, when a non virtual
 function is invoked, the code that gets called is selected based on the type of the pointer ( this is called static
 binding, because the call is resolved at compile-time )

 Dynamic binding causes functions to be called through a pointer ( vtab ), static typing guarantees that there is
 good code on the end of the pointer.

 Virtual Destructor:
 If anyone anywhere needs to delete a derived class object using a base class reference, then the base class
 destructor needs to be virtual. If a base class has any virtuals, then it needs to have a virtual destructor as well
 . If the base class does not have any virtual, then the class designer wasnt planning to use the class as a base
 class. Because virtuals use a virtual table pointer, hence per object space does not vary much if there is one
 virtual function or many virtual functions. Hence it is advisable to use a virtual destructor. Destrutors are called
 when the object does not have any reference or when the destructor is called explicitly using delete keyword. The
 destructors are particularly important for example closing a shared file or unlocking a semaphore. If the base class
 has a virtual destructor as a pure virtual function, it is needed to define the destructor elsewhere, because
 otherwise, there would be a linker error when the derived class is destructed. The reason is that the derived
 destructor automatically calls the base destructor.

 Base* base = new Derived; This means that base is a pointer to the type Base and contains the address of the Derived
 type. This is a valid statement. Base pointers / references can be assigned to their derivatives.

 The sequence of the destructor is exactly the opposite of the constructor. First the derived class object is
 destructed and in the reverse sequence as the member data are declared in the class body. Then the non virtual base
 class object is destructed. For virtual base class, the destructor of the base class is only called, when the most
 derived object is destructed. Hint - diamond shaped multiple inheritance.


 This pointer:
 This pointer in a class has a type "pointer to the class". If it is invoked in the member function of the class and
 the member function is const, then the this pointer has a type "const pointer to the class"

 Scope operator:
 The purpose of the scope operator is to bypass the dynamic binding mechanism. Hence a syntax like
 Derived d; d.Base::f() will call the Base virtual function instead of the Dervied virtual function. Its advisable to
 use scope operator instead of the this pointer.

 Always use array class and not array type for passing array of derived objects to the base reference. This is
 because, the array class has further checks about the indices and run time errors such as index out of range can be
 avoided.

 Overloading and overriding behaviour between directly using the dervied pointer and using base pointer pointing to a
 derived object must be the same.

 Incremental programming - bits representation ( data ) and mechanism ( function ) is inherited. Default parameter in
 the virtual member function in the base class should be the same in the virtual member function of the derived class
 . Apparently, the default parameter is not forwarded, but just the code is forwarded.

 #157 Dynamic Typing:
 Switch case and if / else statements leads to "code finds the code" way of coding. This is called dynamic typing.
 The dynamic typing should be avoided and instead dynamic binding should be used. Dynamic binding refers to virtual
 functions. Ofcourse a program cant have a static knowledge of the things that existed before the execution of the
 program, which forces the developers to use the dynamic typing with switch/case statements. However, with a little
 bit of more creativity and design, virtual functions can be used. This also helps to avoid downcasts ( a pointer
 cast used to convert a base pointer into a dervied pointer object ). -
 Example downcasting: (Derived&)baseObject.memberFn();

     void printItalics(BasePrinterClass &base, const char *s) // global function accepting base or derived objects.
     Depending on the parameter passed ( dynamic typing ) the code is executed.
     {
         switch ( which_derived_object ) // calls non virtual functions
     }
     void printItalics(BasePrinterClass &base, const char *s)  // virtual functions defined inside the class and the function is called depending
     on the object with which it is bound to.
     {
         base.italics(const char *s)  // italics is a virtual function in each derived class
     }

 Macros and function calls
    #define minMacro(i,j)    (i) > (j) ? (i) : (j)
    val = minMacro(get_i(), get_j())

    int minFunction(int i, int j) { return (i) > (j) ? (i) : (j); }
    val = minFunction(int i, int j) { }   // this will give a correct result

 #168 Constructors and Destructors:


 Constructors provides the ability to think to existing objects. This means first an object is created and then a
 constructor is immediately called, that initialises this object in a meaningful way.
 Destructor shreds the objects after it has died. It takes away the ability to think from the object. Its like
 digging a grave for a person who is already dead. The death of an object can occur in many ways:
 1. temporary block {...} ends
 2. delete is called
 3. main ends where the object was created

 One can explicitly specify the base class in the derived constructor. But it is not important, as the base class
 constructor will be called implicitly. Derived(int radius = 0 ): Base(), _radius(radius)

 It is worth mentioning that constructors can only call constructors from their immediate parent/base class.
 Consequently, the C constructor could not call or pass parameters to the A constructor directly. The C constructor
 can only call the B constructo r (which has the responsibility of calling the A constructor).
 There is an exception in case of diamond shaped multiple inheritance when the constructor can be called
 by a non immediate derived class, because otherwise, it would not be clear who should call the parent construtor.
 This is one time when the non immediate derived class is allowed to call a non-immediate-parent constructor directly
 . The virtual base class constructor is called before a non virtual base class constructor. That the most derived
 class is responsible for creation of the virtual base class it not only valid in a diamond scenario, but also when
 the most derived class inherits a virtual base class in single inheritance.

 The nutshell is that the virtual base class is never created by the class that inherited the virtual base class,
 but is created by the most derived class.

 Virtual Constructor:
 Virtual constructors do not exist. The simple reason is that constructors are used to create objects. They are like
 machine in a factory churning out a product. Hence, at the time of instantiation of the object, the constructors
 needs to be known. Thinking of constructors as member functions attached to an existing object is the wrong mental
 mode, instead think of them as factories that churns out objects. The virtual table is a pointer table that points
 to member functions ( base or derived or derived derived etc. ) . Since constructors are not member functions, it is
 not possible to make them as virutal.
 The Big Three:

 Destructors, Copy constructor and the assignment operator are the big threes. When the program does not explicitly
 defines it, then the compiler synthesises them in the background. So, X a; and X b = a; and X b; b = a; are all
 valid statements irrespective of if the class has defined them explictly. The first one calls a default constructor,
 the second one calls the copy constructor and the third one calls the assignment operator. When a class uses a plain
 T* to implement remote ownership, forgetting any of the Big Three will lead to generation of the wrong code. The
 compiler synthesises constructors and assignment operators automatically if it doesnt find one. Therefore it is
 better to use a managed pointer. Assuming a HeapPtr<Class> ptr; declared inside a class X(). Normally, the compiler
 will try to synthesize this ptr via copy constructor or assignment operator. However, when it sees, that the ptr is
 not a raw pointer but a managed pointer and that the class that is managing the pointer already has a copy
 constructor / assignment operator for the pointer, then it will silently not do anything. Had this been a raw
 pointer, like Class *ptr, then the compiler would have forced to create the copy constructor and assignment operator
 for this class object.
 Ofcourse, when there are more than one objects, such as
     HeapPtr<ClassName> _ptr;
     int abcd;
 then the compiler would synthesise the copy constructors just for the object int abcd and not for HeapPtr<>.
 Hence the moment, ClassName y;; ClassName x; y = x; is called, the compiler generates a compile error.

 When a compiler synthesises the Big Three, then it does it inline. Sometimes, however you would like it to be non
 inline, and hence it is good to write them explicitly.



 Copy constructor:
 Many a times, one would like to simply copy an already instantiated object.
 The copy constructor needs to be defined in the class. If the copy constructor definition does not exist, then the
 constructor cannot be copied as well. Using the copy constructor a class object can be initialised with an already
 available object. That means, the initialisation values are values of the object that is being copied.
 The copy constructor syntax can be
 Class obj2(obj1); Needs X-X reference Class(const Class& //mind, there is no parameter here//) { }
 Class obj2 = obj1; Needs Class& operator=(const Class& class);
 new CopyExample (&objectToBeCopied);
 new CopyExample( *this ) // when the copy is in the class itself.

 Default Constructor:
 This is of the form Class() { };
 If the base constructor is not called explicitly, then the compiler calls the default constructor written in the
 base class. In the below example, the default constructor has two variables, name and age and both are initialised
 to 0. However, if the base object would have been called by two parameters, then the initialisation would have been
 done according the parameters.

 If no base class constructor is specified, the default base class constructor will be used. In that case, if no
 default base class constructor can be found (or created by default), the compiler will display an error.

     Person(std::string name = "", int age = 0)
        : m_name(name), m_age(age )

 Person person1;   // Default constructor will be called
 Person person2 = Person();
 Person person3("Foo", 50); // the default constructor can have arguements, but the conditions is that the arguements
 should have a default value in the definition of the constructor. Please see below


 bool operator>(const Cents &c1, const Cents &c2)

 Consider the expression std::cout << Point. If the operator is <<, what are the operands? The left operand is the
 std::cout object of type std::ostream, and the right operand is the Point class object.

 If you are using a member function instead, the left operand automatically becomes the this object. If you are
 working on a unary operator, then no parameters needs to be passed.

 Although we can overload operator+(Cents, int) as a member function (as we did above), we can’t overload operator+
 (int, Cents) as a member function, because int isn’t a class we can add members to.

 Also operator<< cannot be overloaded with member function, because the left operand is std::ostream.

 Compiler implicitly converts an object prefix into a hidden leftmost parameter named *this


 friend ostream& operator<< (ostream &out, const Cents &cents)
 {
     out << cents.m_cents << " cents ";
     return out;
 }
 std::cout << average(array3, 4) << '\n';

 Friend function:
 Friend a functions is a breather for programmer because they do not have to define the getters and setters for the
 private variables. A friend function allows to access all the private variables of a class and hence gaining two
 important things - one does not have to define public functions for this class. This avoids any other class inheriting
 the class and using the public functions. The friend function is just like a normal function.  A friend function may
 be either a normal function, or a member function of another class.  To declare a friend function, simply use the
 friend keyword in front of the prototype of the function you wish to be a friend of the class.  It does not matter
 whether you declare the friend function in the private or public section of the class. Note that we have to pass the
 parent class object to the friend function. This is because friend function is not a member function. It does not have
 a *this pointer, nor does it have an parent class object to work with, unless given one. It is also possible to make
 an entire class a friend of another class. This gives all of the members of the friend class access to the private
 members of the other class. Here is an example:

    // Make the reset() function a friend of this class
    friend void reset(Accumulator &accumulator);

 This simply means, that reset() can be called from anyone. If we want to restrict reset to be called by a specific
 class, then NewClass::reset() needs to be forward declared in the ParentClass. Another way is to open the ParentClass
 completely by declaring the whole class as friend i.e

    friend class NewClass;

 in the prototype for the ParentClass. Friending is commonly used when defining overloading operators.
 It turns out that there are three different ways to overload operators: the member function way, the friend function
 way, and the normal function way. We’ll first show you the friend function way (because it’s more intuitive for most
 binary operators) and the normal function way. In a later lesson, we’ll cover the member function way (and discuss
 when to use each in more detail).
 impossible :     char c = 'Q';
    std::cout << &c;

 A ClassUsed defined as a friend in another ClassMain gets access to all the private variables of the ClassMain.
 Similarly a FunctionUsed() ( implicitly global ) defined as a friend in another ClassMain gets access to all the
 private variables of the ClassMain.
 But friending is not transitive. A ClassUsed2 defined as a friend in ClassUsed does not get access to the private
 variables of ClassMain. Similarly friendliness is not inherited.
 Friend functions ( not classes ) are however inheritable. i.e a derived class can use the friendliness of the base
 class.

 Friend functions differ from member functions in the way they are used. If an operator overloading such as << is
 declared as a member function, then the class object needs to be the left arguement. This is the only way, the class
 object can access the << operator for example classObject.operator<<. However we want the classObject on the right
 hand side, so that it can be streamed to the output stream cout. If the operator overloading is declared as a
 friend, then the classObject can be positioned to the right hand side. The best example is n.square or square(n). If
 you want to use square(n), then use friend in the function square. If you do not, then you will be forced to use the
 dot operator to access square.


 Const:
 const int* ptr
 int *const ptr
 const int *const ptr
 Both the above can be assigned once i.e during initialisation and its a must that a const object is initialised. An
 uniitialised const object is an error.

 If a class is instantiated as const, the member functions can only be accessed it is declared as const. For example
 int getValue const { return mValue } ; If const is not used, then this member function cannot be called.
 Futhermore, any const member function that attempts to change a member variable or call a non-const member function
 will cause a compiler error to occur. For example: void resetValue() const { m_value = 0; } // compile error, const
 functions can't change member variables.

    void resetValue() const { m_value = 0; }
    void resetValue() { m_value = 0; }

 both are valid and depending on if the class object is instantiated as const, corresponding resetValue would be called.
 Const Expression:
 Expressions that are evaluated at compile time are called const expressions
 constexpr int i = 0;
 constexpr char a = test1("Test", i); // also OK, compile time invocation of test1()
 constexpr char test3(unsigned i)
 {
    return t<i>::value;
 }

 Uniform initialisation, Direct Initialisation, Copy

 BaseballPlayer(std::string name = "", int age = 0,
        double battingAverage = 0.0, int homeRuns = 0)
        : Person(name, age), // call Person(std::string, int) to initialize these fields
            m_battingAverage(battingAverage), m_homeRuns(homeRuns)


 It is worth mentioning that constructors can only call constructors from their immediate parent/base class.
 Consequently, the C constructor could not call or pass parameters to the A constructor directly. The C constructor
 can only call the B constructor (which has the responsibility of calling the A constructor).

 C++ has a third access specifier that we have yet to talk about because it’s only useful in an inheritance context.
 The protected access specifier allows the class the member belongs to, friends, and derived classes to access the
 member. However, protected members are not accessible from outside the class.

 If a member is protected, then the derived class can directly use it from the base class and the base class does not
 need to put any setters and getters for the variable.
    Base &rBase = derived;
    Base *pBase = &derived;


 Virtual:
 Virtual classes - this term does not exist in C++
 Virtual base class - This is used solely during inheritance. A virtual base class cannot be created in itself. But
 its a name given to the class that is inherited by a derived class which inherits the base class with the keyword
 virtual.
 Abstract class -
 Virtual inheritance
 Virtual functions
 Pure virtual functions
 Abstract class - this does not have any member data and all the member functions are pure virtual functions.

 This seems to create another problem too...what if Foo was virtual, and B and C had different implementations of
 Foo? What the heck is D supposed to do when it calls Foo? Is there an actual use case where making A inherited
 virtually solves anything? I mean there must be if this was adopted into the standard, right?


 Inheritance:

 When BaseballPlayer inherits from Person, BaseballPlayer acquires the member functions and variables from Person.
 Additionally, BaseballPlayer defines two members of its own: m_battingAverage and m_homeRuns. This makes sense,
 since these properties are specific to a BaseballPlayer, not to any Person.

 Thus, BaseballPlayer objects will have 4 member variables: m_battingAverage and m_homeRuns from BaseballPlayer, and
 m_name and m_age from Person.

 Inheriting from a base class means we don’t have to redefine the information from the base class in our derived
 classes. We automatically receive the member functions and member variables of the base class through inheritance,
 and then simply add the additional functions or member variables we want. Because Derived inherits functions and
 variables from Base, you may assume that the members of Base are copied into Derived. However, this is not true.
 Instead, we can consider Derived as a two part class: one part Derived, and one part Base. When C++ constructs
 derived objects, it does so in phases. First, the most-base class (at the top of the inheritance tree) is
 constructed first. Then each child class is constructed in order, until the most-child class (at the bottom of the
 inheritance tree) is constructed last. This makes sense: logically, a child can not exist without a parent. It’s
 also the safe way to do things: the child class often uses variables and functions from the parent, but the parent
 class knows nothing about the child. Instantiating the parent class first ensures those variables are already
 initialized by the time the derived class is created and ready to use them.

     Derived(double cost=0.0, int id=0)
         : Base(id), // Call Base(int) constructor with value id!
             m_cost(cost) // Derived member_data

 Note that it doesn’t matter where in the Derived constructor initialization list the Base constructor is called --
 it will always execute first.

 Private members can only be accessed by member functions of the same class or friends. This means derived classes
 can not access private members of the base class directly!

 That gives us 9 combinations: 3 member access specifiers (public, private, and protected), and 3 inheritance types
 (public, private, and protected). Private inheritance makes the base variables private in the derived class.
 Protected inheritance makes the base variables protected in the derived class. Public inheritance does not change
 the access specifier of the inherited variables. In all the cases, private base variables are never accessible,
 irrespective of the type of inheritance.

 When derived.identify() is called, the compiler looks to see if function identify() has been defined in the Derived
 class. It hasn’t. Then it starts looking in the inherited classes (which in this case is Base). Base has defined an
 identify() function, so it uses that one. In other words, Base::identify() was used because Derived::identify()
 doesn’t exist.

 Multiple Inheritance:
 Let’s say we wanted to write a program to keep track of a bunch of teachers. A teacher is a person. However, a
 teacher is also an employee (they are their own employer if working for themselves). Multiple inheritance can be
 used to create a Teacher class that inherits properties from both Person and Employee. To use multiple inheritance,
 simply specify each base class (just like in single inheritance), separated by a comma.
 Ambiguity can result when multiple base classes contain a function with the same name.

 When WirelessAdaptor.getID() is compiled, the compiler looks to see if WirelessAdapter contains a function named
 getID() . It doesn’t. The compiler then looks to see if any of the parent classes have a function named getID(). See
 the problem here? The problem is that WirelessAdaptor actually contains TWO getID() functions: one inherited from
 USBDevice, and one inherited from NetworkDevice. Consequently, this function call is ambiguous, and you will
 receive a compiler error if you try to compile it.

 Solution 1. you can explicitly specify which version you meant to call: USBDevice::getID()

 most of the problems that can be solved using multiple inheritance can be solved using single inheritance as well.
 While most of the issues can be addressed through explicit scoping, the maintenance overhead added to your classes
 in order to deal with the added complexity can cause development time to skyrocket.  Many relatively modern
 languages such as Java and C# restrict classes to single inheritance of normal classes, but allow multiple
 inheritance of interface classes. Many object-oriented languages (eg. Smalltalk, PHP) do not even support multiple
 inheritance.
 The iostream library objects std::cin and std::cout are both implemented using multiple inheritance.

 A virtual base class is always considered a direct base of its most derived class (which is why the most derived
 class is responsible for its construction). But classes inheriting the virtual base still need access to it. So in
 order to facilitate this, the compiler creates a virtual table for each class directly inheriting the virtual class
 (Derived1 and Derived2). These virtual tables point to the functions in the most derived class ( MostDerived ).
 Because  the derived classes have a virtual table, that also means they are now larger by a pointer (to the virtual
 table).


 Friend:

 There’s one bit of trickiness that we can run into when trying to call friend functions in base classes, such as
 operator<<. Because friend functions of the base class aren’t actually part of the base class, using the scope
 resolution qualifier won’t work. Instead, we need a way to make our Derived class temporarily look like the Base
 class so that the right version of the function can be called.
 Virtual Function:

 The concept of virtual functions is an important part of polymorphism. The whole idea is based on the fact that in
 object-oriented programming, when a derived class inherits from a base class, an object of the derived class may be
 referred to via a pointer or reference of the base class type instead of the derived class type. The derived object
 is referred via a pointer or reference of the base class and this gives certain advantages to the programmers.

 Virtual functions are resolved late i.e the binding is not yet known at the compile time. In a normal function
 ( without virtual ) the binding is early, because the compiler already knows that member function would be called
 and hence the call to the address is already designated. Virtual functions allow a program to call methods that
 don't necessarily even exist at the moment the code is compiled. It could be possible that the there is a
 overriden function in a derived class in one of the library that is linked at linking stage or an overriden
 function comes from a run time library. One point to note with respect to the virtual functions called in the
 constructors is that the constructors ignore the dynamic binding of virtual functions. The reason is simply as
 stated in the section Constructors is that the constructors give life to an object. One cannot go into the virtual
 world, when the object itself is not real. The same stands for destructors. By the time, the base class destructor
 is called, the derived object is already buried. Hence, it makes sense to call the native virtual function of the
 base class and not look for the derived version of the virtual function.

 The modifier ( virtual ) is inherited by all implementations of that method in derived classes, and hence it is not
 strict to prepend the modifier again in all the overriden derived member functions. Only the most base class
 function needs to be tagged as virtual for all of the derived functions to work virtually. However, having the
 keyword virtual on the derived functions does not hurt, and it serves as a useful reminder that the function is a
 virtual function rather than a normal one. Consequently, it’s generally a good idea to use the virtual keyword for
 virtualized functions in derived classes even though it’s not strictly necessary.

 Since most of the time you’ll want your functions to be virtual, why not just make all functions
 virtual? The answer is because it’s inefficient – resolving a virtual function call takes longer than resolving a
 regular one. Furthermore, the compiler also has to allocate an extra pointer for each class object that has one or
 more virtual functions. We’ll talk about this more in future lessons in this chapter.

 A virtual function is a special type of function that, when called, resolves to the most-derived version of the
 function that exists between the base and derived class. This capability is known as polymorphism. A derived
 function is considered a match if it has the same signature (name, parameter types, and whether it is const) and
 return type as the base version of the function. Such functions are called overrides. It is not mandatory to add
 virtual keyword everytime in the derived version. It is enough to write it once in the base class. However, it is
 good coding guideline to mention virtual in the derived member functions too.

 Normally, the base reference to a derived class ( Base &rBase = derived ) can only call a base member function.
 But, if we define the base member functions as virtual, then it looks in the derived part and calls the most
 derived function. This works because every class maintains internally a virtual table. Hence, it takes a little
 bit more time, if a virtual function is called. This also infers that a constructor or destructor cannot call a
 virtual function. This is because, the derived constructor is only called after the base constructor. If there
 is any function call in the base constructor that is virtual, then it would go on to look for the derived version.
 However, the derived version is not yet ready, because the derived constructor is not yet been called. Always make
 your destructor virtual when you are dealing with inheritance.



 Pure Virtual Functions: Pure virtual functions are functions that makes a class abstract. A pure virtual function
 simply acts as a placeholder that is meant to be redefined by derived classes. An pure virtual class cannot be
 instantiated. It can only be derived. Another method to avoid instantiation of a class is by making the constructor
 private or protected. However, the theory of pure virtual function is that the class has got no constructor and
 hence cannot be instantiated at all even from a derived class. Pure virtual functions are just prototypes. The
 derived class is responsible to implement “all” functions prototyped in the base abstract class ( also called pure
 virtual class or an interface class ) and if the derived class does not implement any of the function, then a
 compile error is thrown. The body of a pure virtual function has to be made outside and should not be inline.

 Interface class: Interface class is one example of a pure virtual class. It is just a collection of pure virtual
 functions. It is not allowed to have non abstract member functions in an interface class. It is also not allowed to
 have member variables. Due to its popularity, some languages such as java has defined interface keyword, so that
 the class is explicitly defined as interface, without makiing all the member function as abstract.

 Override and Final: Override is an identifier and tells that the functions are not native implementations, but has
 been derived from a base class. This prevents typos and the programmer would get an compile error, if he was
 willing to create a derived version of a function call, but actually missed something ( for example the name of
 the function was slightly different ). The compiler will complain then that this type of function does not exist
 in the base class. If final is used after override, no more override is allowed. An overridden function with no
 virtual counterpart in the base class does not make any sense and the compiler will throw an error - Error:
 marked ‘override’, but does not override.

 Pointers

 int val = 10; // val is an integer
 int const val = 10; // val is a constant integer
 const int val = 10; // val is a constant integer .. this versin is preferred. leftmost keyword defines the variable
 int *val; // val is a pointer that points to an integer
 int const *val; // val is a pointer that points to a constant integer
 const int *val; // val is a pointer that points to a constant integer
 int * const val; // val is a constant pointer that points to an integer
 const int * const val; // val is a constant pointer pointing to a constant int. Invoke using &val
 const char* const argv[] // argv is an array of constant pointers. The pointers point to a constant char. Invoke using &argv[]
 int const * const val; // val is a constant pointer pointing to a constant int


 void const_fn (int a, int b ) const {  }
 void non_const_fn (int a, int b )  {  }

 const Base &base;
 So, as we have already learnt, the compiler won’t let us call any functions that do not have the "const" keyword.
 base->non_cost_fn(); // error


 int value = 5;
 const int *ptr = &value; // ptr points to a constant integer. This is OK, although value is not a constant integer
 *ptr = 6; // not allowed

 int value = 5;
 int *ptr = &value;
 *ptr = 6 // allowed

 const int value2 = 10;
 int *ptr2 = &value2; // ptr2 points to an integer and is not allowed.

 int value = 5;
 int * const ptr = &value; //ptr is a constant and once initialised cannot be reinitialised.
 ptr = &value2 ; // not allowed
 *ptr = 6 ; // ofcourse this is allowed because the value itself is not a constant.

 Finally , A const pointer to a const value can not be set to point to another address, nor can the value it is
 pointing to be changed through the pointer. :) Hint for readability. Just remember that the type of value the
 pointer points to is always on the far left.

 There are two kinds of pointers: Raw pointer and Managed Pointer. The raw pointer is simply pointing to a location
 in the memory and can only be deleted by the delete keyword. It does not live in a container. Managed pointers live
 in a container and many actions can be done on the pointers. Most notably are destructing the pointer and the
 referent ( the object that the pointer is pointing to ) automatically.

 One should always use managed pointers like std::unique_ptr. Avoid std::shared_ptr although they are managed. The
 reason is that the shared_ptr allow to copy the pointers and hence can lead to dangling pointers after
 improper destruction.

 A very important thing is that * can only be used on basic data types. It is not possible to dereference a pointer
 of std::array<int,3> type with a *. However it is possible to dereference an int array[x][y] with *. For std::array
 or any other c++ class pointer, corresonding methods should be provided such as data() or data in case of std::array.

 Remote ownership:
 When the object that owns a pointer also owns the allocation pointed to by that pointer, the object is said to have
 remote ownership. That is the object owns the referent. And when the object has remote ownership, it is also
 responsible for deleting the referent.


 References:
 So, as C defines the terms, an lvalue is a kind of expression (something that exists in C source code), but an
 rvalue is the result of evaluating an expression (something that exists during program execution).

 Three kinds of references. References to non const values. References to const values often called const references
 and rvalue references.

 References are just aliases. Instead of using the variable name, one can simply use the reference name for accessing
 or modifying the variable. Just as addresses can be printed by using the & operator, the references can also access
 their address using the & operator. There is no difference between a variable and the reference to a variable.

    int value = 5;
    int &ref = value;
    int &invalidRef; // references must be initialised to something

    const int value = 5;
    int &ref = value; // Not allowed just like in pointers, otherwise ref can change the value.
    const int &ref = value; // Allowed, this is reference to const values or also called const references.

    int value = 5;
    const int &ref = value; // this is OK, since the reference is placed in the const memory.
    value++; // allowed
    ref++; // not allowed

    const int &ref = 2+3; // allowed

 References ( not const references ) cannot refer to a rvalue ( temporary value ) or a const lvalue. However,
 const References can refer to a rvalue and a lvalue ( both const and non const ) . Hence const references can be
 applied everywhere. References to const values are particularly useful as function parameters because of their
 versatility. A const reference parameter allows you to pass in a non-const lvalue argument, a const lvalue argument,
 a literal, or the result of an expression.
 In case, the arguements needs to be changed, then pass using non const references, otherwise pass using const
 references. A restriction is that rvalues can be assigned to only const reference. A lvalue can be assigned to
 both const reference and reference.

 In the above code, getName() will return a pointer to C-style string “Alex”. This is okay since “Alex” will not go out
 of scope when getName() terminates, so the caller can still successfully access it.

 The answer is that std::cout makes some assumptions about your intent. If you pass it a non-char pointer, it will
 simply print the contents of that pointer (the address that the pointer is holding). However, if you pass it an object
 of type char* or const char*, it will assume you’re intending to print a string. Consequently, instead of printing the
 pointer’s value, it will print the string being pointed to instead!

 As a general rule,

 Use references in function parameters and return types to define useful and self-documenting interfaces.
 Use pointers to implement algorithms and data structures.
 The major difference between pointer and reference is that pointer ( not const pointer ) can be reassigned during its
 life time and the references cannot.
 int *const p = &i; and int &r = i; is literally the same. One cannot omit the assignment, because it will be a compile
 error. Reason is that the variables r and p would be dangling if it is not assigned to some object.

 Rebinding a reference is not possible and also assigning a const pointer to another object also not possible.
 const pointers can be NULL, but references cannot be NULL. Thats why, the references are mostly used as fucntion
 parameters, because the called can never pass NULL. However, indirectly passing NULL is possible for example storing
 the NULL in a pointer and then passing the pointer object to the reference. Anoter way to pass NULL is when an object
 is deallocated ( for eample the function returns and all the automatic variables disappear ) .

 A qualified name is one that specifies a scope for example std::cout - here cout is a qualified name.

 Within choosing pass by value or pass by reference, pass by
 reference is preferred, because otherwise we will have copies of the objects on the heap. The best is to declare const
 references.

    int (&xFunc)() = funcX; xFunc() is an alias for funcX

 When a function returns a reference, the function call becomes an lvalue for the referent. This is normally used to
 allow operator expressions to be used as lvalues - the subscript operator, the dereference operator, and so on.
 functioncall(); = referent in the function i.e what is the reference referring to inside the function,

 Scope:

 Static data and functions inside a class are shared among all class objects. They can be accessed the way just another
 non  static data member or member function is accessed. The only difference is, that the static members retain their
 values and the  non static members have values depending on the class they are called.
 Another way to access static data member and functions is using the scope resolution operator. One can think static
 data and member functions as obdachlosen. They are not linked to any house and can be accessed by anyone. They also
 do not come under access control, hence they can be put anywhere ( private, public, protected ) and they are still
 accessible via the scope resolution operator or class objects. The static data is therefore default public. The
 static member and member functions when declared inside a class is just a kind of forward declaration. They have to
 be explicitly defined outside the class, because static member variables are not a part of the individual class
 objects. Mostly, the class is declared in the header file and the static members are defined in the cpp file. There
 is one excetion however, when the static values can also be defined within the class. This is when the static member
 is declared to be a const. This is called inline initialisation of static member variables.

 We said, that the static variables should be defined outside the class. This is not a good way to write a program,
 because in an object oriented programming, most of the data and initialisation is hidden. Constructors are meant to
 initialise and they are hidden. Similarly static member initialisation should also be hidden. The hiding of
 initialisation of static member data is possible, if the static object is initialised in a different class. So a
 sequence of nested classes can achieve the initialisation of static variables.

 Although static members can be accessed by the class object, this is discouraged. The perfereable way is to access
 the static member data via a scope resolution operator or the static member data can also be accessed by a static
 member function.
 One good example of the usage of static objects inside a class is when a count of number of objects of the class is
 required. Everytime a constructor is called, the static data increments and everytime a destructor is called, the
 static data is decremented. Ofcourse, one should make sure, that this static member data is not incremented or
 decremented elsewhere, which technically is not a problem at all.
 One word of caution is that the static objects needs to be initalised before it is used. Technically, it is possible
 that the static data is used before it is initialised. Proper care should be taken to avoid the situation.

 Static member functions cannot access non static data.
 Pure static class:
 A pure static claass is class whose all members are static. A word of note - pure virtual class is called abstract
 class. Pure virtual function is when a function is initialised to 0.


 Class scope static objects
 File scope static objects
 File scope global objects

 TYPEDEFS and #DEFINES

    typedef int* int_p1;
    int_p1 a, b, c;  // a, b, and c are all int pointers.

    #define int_p2 int*

    int_p2 a, b, c;  // only the first is a pointer!

    typedef int a10[10];
    a10 a, b, c; // create three 10-int arrays
    int a[10], b[10], c[10];
    typedef int (*func_p) (int);
    func_p fp; // fp is a pointer to a function that takes an int and returns an int
    int (*fp)(int)

 Usually, typedefs are the way to go as they are so much less error-prone. In which case you could use using = as well
 but that's personal preference since they're both the same:

 The only difference between both prototypes is the use of either the keyword class or the keyword typename. Its use is
 indistinct, since both expressions have exactly the same meaning and behave exactly the same way.

 #define is a symbolic constant.
 #ifndef CONSTANTS_H
 #define CONSTANTS_H

 // define your own namespace to hold constants
 namespace constants
 {
     const double pi(3.14159);
     const double avogadro(6.0221413e23);
     const double my_gravity(9.2); // m/s^2 -- gravity is light on this planet
     // ... other related constants
 }
 #endif

 using declaration and using directive

 typedef int &ref_to_int; ref_to_int const r = i;

 Typecasts:
 static_cast : for anything other than base and derived pointer
 const_cast : convert constness
 dynamic_cast : for base and derived pointer
 reinterpret_cast:

 Exception:
 We assert a statement. i.e assert(true) is OK. But assert(false) will trigger an exception. If the condition inside
 the assert is correct, then no exception will be thrown.
 assert(found && "Car could not be found in database"); // Add a string
 static_assert(sizeof(long) == 8, "long must be 8 bytes"); This is triggered only at compile time.

 std::vector:
 A vector is a dynamic array with automatically handled storage. The elements in a vector can be accessed just as
 efficiently as those in an array with the advantage being that vectors can dynamically change in size
 vector<int> v1 = {1,2,3,4} // size is 4
 vector<string> v2; // size is 0
 vector<Shape *> v3(23) // size is 23 and default init value is null, since the type is a pointer.
 vector<double> v4(23) // size is 23 and the default init value is 0, since the type is not a pointer.
 vector<double> v4(23,9.9) // size is 23 and the default init value is 9.9

 std::array:
 std::array is a container that encapsulates fixed size arrays. Unlike A C-style array, it doesnt decay to T*
 automatically. As an aggregrate type, it can be initialized with aggregrate-initialisation given at most N
 initializers that are convertible to T.

 Compiler Options:
 -std=c++11
 -std=gnu++11
 -fexception

 Aggregrates:
 Aggregrates is an array or a class ( struct , union inclusive ) with
 - no explicitly user declared constructors ( default, non-default and copy constructors ). Aggregrates can have user
 defined  assignment operator though.
 - only public data members.
 - no base class
 - no virtual functions.
 - An array is an aggregrate even if it is an array of non aggregrate class type.
 A special thing about aggregrates are that they can be initialised with curly braces { }. Non aggregrates cannot be
 initialised with curly brackets.
 Initialisation of aggregrate array is simple. Simply use the curly brackets to initialise them.
 Initialisation of aggregrate class is complex. The elements in curly brackets are assigned one to one in the order
 of the public data members that appear in the class declaration. Memberwise initialisaton with braces implies that
 the class is nothing more than the sum of its members.
 In C++11, one can have a user defined default constructor. But it just points to the default constructor.
 Aggregate() = default; // asks the compiler to generate the default implementation
 Also, any kind of inline initialization of the data members in the class declarations, such as int x = 5; violates
 the principles of an aggregrate. Such kind of inline initialization is similiar to a user defind default constructor
 when the class is instantiated.
 Aggregrate initialisation can be folded in during compile time. For example std::array is a compile time type and
 hence needs to be work with aggregrate initialisation.

 PODs ( Plain Old Data :
 If a class is not an aggregreate, then it is definetly not a POD. A POD is a special type of aggregrate with few
 more constraints. As we saw, that an aggregrate can consist of assignment operator.  A POD on the other hand
 - has no user defined copy-assignment operator
 - none of its non static data members is a non POD class. As soon as the any of static data members is a non POD class,
 then the POD class is not a POD anymore.
 - none of the non stattic data members are references.
 - none of the non static data members are array of non POD class.
 - should not have a user defined destructor. The aggregrates allow a user defined destructor.
 In a nutshell it means, that the PODs cannot consist of any hint of non PODs. This is different from aggregrates,
 where the aggregrate class can be an array of non aggregrates.
 A POD is closest to C struct, with additional member functions. PODs are optimum for potability in dynamic libraries
 . They are often used as portable dynamic library. The lifetime of a POD ends with the release or reuse of the
 storage, unlike Aggregrates, where the execution of the destructor ends the lifetime of the object. Memcpy from the
 POD type object to a array of char and back, will not alter the object. This cannot be gauranteed for the non POD
 type. A struct memcpy to an array and back will reveal the original struct again for example. Additionally member
 functions in a POD type extends the struct kind of objects.

 Randomize:
 Standard Library introduces two kinds of random generator. One that is with a global seed and one that takes an input
 parameter directly with each randomization.
 rand ( srand ) , drand48 ( srand48 ) for example require a seed, where in erand48 does'nt require a seed.
 Pseudorandom number generator.
 std::srand() - sets the seed
 std::generate, std::generate_n, std::nrand()
 Fischer-Yates Shuffle, std::generate_random()

 std::generate(array, array + sizeof(array)/sizeof(int), ::rand);
 std::transform(array, array+SIZE, array, std::bind2nd(std::modulus<int>(), 255));

 srand( unsigned( time(NULL) ) );
 random_shuffle(array, array+5);

 std::string uniqueName() {
    auto randchar = []() -> char
    {
        const char charset[] = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
        const size_t max_index = (sizeof(charset) - 1);
        return charset[ rand() % max_index ];
    };
    std::string str(4,0);
    std::generate_n( str.begin(), 4, randchar );
    return str;
 }

 Big O Notations:

 Computational complexity theory is the branch of computer science that focuses on classifying computational problems on
 the basis of their inherent difficulties, and relating those classes to each other. One of the roles of compuationanal
 complexity theory is to determine the practical limits of what computers can and cannot do. The theory formalizes
 the intuition, by introducing mathematical models of compuation such as time, resource, number of gates in a circuit
 ( used in circuit complexity ), number of processors ( used in parallel computing ). It is believed, if the problem
 can be solved by an algorithm, there exists a Turing machine that solves the problems. The most commonly used
 model is the Turing machine. In the Turing machine, the computational complexity and time to execute is simply done
 by read, access, write and moving the head pointer to the next block. Basically, the turing machine is an infinite
 tape.

 A template requires a constant expression for a non-type parameter. For a const variable to be used in a constant
 expression, its initialization must be visible to the compiler. So you'll probably have to include header1.hpp in
 header2.hpp.
 image_manual_bare1’ was not declared ‘constexpr’
 the value of ‘image_manual_bare1’ is not usable in a constant expression


 Standard Library terms:

    Containers

        basic_string
        bit_vector
        bitset
        char_producer
        deque
        hash
        list
        map
        multimap
        multiset
        priority_queue
        queue
        rope
        set
        slist
        stack
        vector

    Iterators

        back_insert_iterator
        bidirectional_iterator
        bidirectional_iterator_tag
        forward_iterator
        forward_iterator_tag
        front_insert_iterator
        input_iterator
        input_iterator_tag
        insert_iterator
        istream_iterator
        iterator_traits
        ostream_iterator
        output_iterator
        output_iterator_tag
        random_access_iterator
        random_access_iterator_tag
        raw_storage_iterator
        reverse_bidirectional_iterator
        reverse_iterator
        sequence_buffer

    Algorithms
    Functors
    Utilities
    Adaptors
    Allocators
    Polymorphic allocators

 Auto keyword -  For variables, specifies that the type of the variable that is being declared will be automatically
 deduced from its initializer. For functions, specifies that the return type is a trailing return type or will be
 deduced from its return statements (since C++14).

 for loop - 
 Executes init-statement once, then executes statement and iteration_expression repeatedly, until the value
 of condition becomes false. The test for condition takes place before each iteration.
 An init statement can be a null statement. It can be an expression statement. It can be a declaration with
 initializer and there is no limiit to the number of declarations. The init statement must end with a semicolon. The
 series of expression statements are sepearated by a comma.

 Condtitions are expressions that are contextually convertible to bool.
     for (int i = 0, *p = &i - this is multiple declaration; i < 10 condtion contextually converts to bool; ++i)
     for ( int ee; cin>>ee; ) {} Here Entry is a declaration without initializer. cin >> ee is an expression that
     contexually converts to a bool, if the user has returned without inputing any text. This line simply outputs
     infinelty a number on the input unless, the user presses return two times.

 a declaration of a single variable with a brace-or-equals initializer. the initializer is evaluated before each
 iteration, and if the value of the declared variable converts to false,
 the loop is exited.
    for (int n = 0; char c = cstr[n] - a declaration of a single variable is also a condition ; ++n)

 Auto
     for (auto iter = v.begin() - init can be used as auto ; iter != v.end(); ++iter)

 Type of statements in CPP - one is the exreppsion statement and the other is a return statement.
 Conditional expressions are contextually convertible to bool.
 Operand can either be left side operand or the right side operand. In some cases, there is only one operand.
 Operators work on operands.


 Range based loops are loops, where there is no indexing.
 If all the elements in a container needs to be parsed, then it is adivsable to use a range based for loop.

 range declaration -  a declaration of a named variable, whose type is the type of the element of the sequence
 represented by range_expression, or a reference of that type.

 range expression -  any expression that represents a suitable sequence ( either an array or an object for which
 begin and end member functions or free functions are defined or a braced init list. range expression is evaluated to
 determine the sequence of the range to iterate.
  std::vector<int> numbers = { 1, 2, 3, 4, 5, 6, 7 };
     for ( auto xyz : vector ) // xyz = vector[x] and hence the type is either int, double float etc.
        cout << xyz << '\n'
     for ( auto xyz : map) // xyz = map[x] and hence the type is a std::pair. The map should be like int,int


 Iterators -
 The Iterator concept describes types that can be used to identify and traverse the elements of a container.
 Iterators can be thought as an abstraction of pointers.
 Given

 Containers -
    vector
    list
    forward_list
    deque
    set
    multiset
    map
    multimap
    unordered_map
    unordered_multimap
    unordered_set
    unordered_multiset

 Collection of values and then manipulating such collections are done in classes with the main purpose of holding
 objects that can be manipulated. These classes are called containers.

 Map -
 if the key isnt found, it is entered into the map with a default value for its value. The default value for an
 integer type is 0.

 Unordered Map -
 The cost of a map lookup is O(log(n)) where n is the number of elements in the map. This means, we perform only
 about 20 comparisons to find an element. It is still better to do a hashed look up instead of using an ordering
 function such as <.  The standard library hashed containers are referred to as unordered, because they dont require an
 ordering function, such as comparison with <.

*/



/**
 wprintf
 fwprintf
 swprintf
    prints formatted wide character output to stdout, a file stream or a buffer
 vprintf
 vfprintf
 vsprintf
 vsnprintf
    prints formatted output to stdout, a file stream or a buffer
using variable argument list
fputs
    writes a character string to a file stream
 scanf
 fscanf
 sscanf
    reads formatted input from stdin, a file stream or a buffer
 to_chars
    converts an integer or floating-point value to a character sequence


 */

