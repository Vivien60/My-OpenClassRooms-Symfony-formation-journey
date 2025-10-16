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
- ___correct implementation (test return each stage, etc) : no fast & furious rush forward___
- ___avoid implementing multiple method at a time before testing functionality : implement one methoid, test, and again.___

One thing I forgot : I tried my best to implements method I need, after creatin my MCD then my DB. But, I didn't create the carrdinalities and the properties in my model. Methods implicitly show them. But I should have note this in the property. 
<br/>For example, my User are owners of books. In Books, I have an ownerId and an Owner.  In User, I don't have any colelction of Book associated... what a shame !
<br/> __Next time , when conceiving class, I will do that FIRST !__

<ins>New day :</ins><br/>
I don't know if it's a symptom or a code smell, but : __I'll rember to put default value for my property, or initialize all of them in__ ____construct, that's really too ... cumbersome to not do that__

<ins>New day : 16/10/2025</ins><br/>
_should chek english formatting date ^^'_
There's have been 9 days 'til I come back. Busy, etc... So, yesterday I think at something I'll need to remember :
__Don't pass directly your request data to your model__ 
I was trying to find out what my input names should be in my view. So I wen to my controller, see I pass directly all request param to my model class (with $_REQUEST). I was feeling bad, then I go to my model class... and I felt nauseous 🤢 I need to look at my class properties to know the names of my form fields... My view and my model was coupled ! 
<br/>If I wanted to change my class property, I should change my field name. Well, if I need too, I could make my controller play its role and hide that change from my view. But that give a cost to a simple change, wich occurs inside the privacy of a class. Actually, if I change a property, my controller is affected. So privacy is not the goo term. Depends on how class interface has been made.
<br/>So, is it so problematic ? Yeah, I don't want my view being couplesd to my model, I don't want a change of my model affect that much my view. Actually, it's not really the change... because model property change affect my view, as its instance is  used by it. So they are lightly coupled, but only for the reading access, not the writing one. Object are not updated or created by the view.
<br/>Anyways, as I was saying, that's not the change itself the problem, that's the ENCAPSULATION. To know the field name, I need to go inside my model. That breaks encapsulation. You shouldn't have to go through another layer which is distant/decoupled, (ok, half distant/decoupled) thanks to the controller. __Controller is the chaperone that prevent view and model being to touchy together, being "coupled" :) But it also hide some model details from the view, which help to the decoupling finally. It encapsulates the building mobject method. If detail of my building method affect view, that's encapsulation breaking__
