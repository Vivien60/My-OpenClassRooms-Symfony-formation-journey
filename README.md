# My-OpenClassRooms-Symfony-formation-journey
Here is some thoughts I'll write durning my formation at OpenClassrooms on Symfony Developer for 1 year. I'll try to keep it in english, but sometimes when I'll be overwhelmed I can't promise I won't speak french ! And I can't promise it will be a good english also ^^'

## Project 6 : TomTroc

I've finally entered into the first project from scratch with MVC into that formation : the TomTroc app from the 6th project.
I'm wondering if I structured it correctly by thinking my progression mostly by entities/module, without making true UI at first :
1. basic structure
2. basic implementation Controller/View
3. User universe : sign-in, signup, profile, session, etc...
4. Book universe : book copy detail, user's library into profile page, book copy edition
5. Messaging universe : Thread, Message, etc...

And some back and forth between all these steps. Each time I created first controllers's actions and routes, then view class, then model methods, then controller action implementation with model methods.

But I remember what's said by Venkat Subramaniam in the video "Core Design Principles for Software Developers" : that you shouldn't create every class staight away before making another one then try to associate them. You make some back and forth between them to keep good cohesion, as you would when you mount a furniture : you don't totally screw one side then anoher, you screw progreesivlely each side, a little one, then a little for the other one, then back to the first one, to keep good structure overall. And I'm wondering if I did not screwed to much at first !

After some hours with review and fixes, I think now I'm quite correct with this, but I've to do better with :
- correct implementation (test return each stage, etc) : no fast & furious rush forward
- avoid implementing multiple method at a time before testing functionality : implement one methoid, test, and again.

One thing I forgot : I tried my best to implements method I need, after creatin my MCD then my DB. But, I didn't create the carrdinalities and the properties in my model. Methods implicitly show them. But I should have note this in the property. 
For exzample, my User are owners of books. In Books, I have an ownerId and an Owner.  In User, I don't have any colelction of Book associated... what a shame !
