## 2026-04-03

Today I'll focus on continuing to learn Rust.  There is also an interesting problem at PxD work today; can we find out when there are message delivery problems on the receiving end of our messages?  The specific problem is that once we send the message to the telco, there is no guarantee the user will receive it.  There have been numerous recurring instances when this has happened, and there is no clear way to receive alerts since there are no guarantees on message delivery receipts from our telco or the user's telco.

Therefore, is there some other way that we can find out if the message was received?

I suggested to the team that we send an SMS followup message after every IVR push.  Since SMS is a different, and simpler protocol, it is not likely to fail in the same way.  We could then use this as a marker to indicate which calls are "most probably" valid and which are most probably experiencing issues.  Doing some statistical magic we can then adjust the engagement and listening rates appropriately.

I'll work on this problem some more to figure out if there are some solid statistical methods we can use to help identify when calls aren't being received and/or how we can appropriately mark the data.