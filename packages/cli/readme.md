# shadcn-chat

A CLI for adding **chat** components to your project.

# Installation

> Some of the components rely on [shadcn-ui](https://ui.shadcn.com/docs/installation), so make sure to have it installed.

# add

Use the `add` command to add components to your project.

It is recommended to install all components at once:

```
npx shadcn-chat-cli add --all
```

To view a list of all available components run the following command:

```
npx shadcn-chat-cli add
```

Otherwise, install individual components by running:

```
npx shadcn-chat-cli add [component]
```

![image](https://github.com/user-attachments/assets/8d9d2b33-b3ce-45f4-85b9-40b49497a9a6)

The components will be installed in a subdirectory of the `components` folder: `src/components/ui/chat`

# Usage & Examples

All of the below primitives are unstyled and you can add styling in any way you'd like - for instance with `className`.

## Chat components

This is an example of how to quickly build stunning Chat UIs.

```
import { ChatMessageList } from "@/components/ui/chat/chat-message-list";
import { ChatBubble, ChatBubbleAvatar, ChatBubbleMessage } from "@/components/ui/chat/chat-bubble";
import { ChatInput } from "@/components/ui/chat/chat-input";

<>
  <ChatMessageList>
    <ChatBubble>
      <ChatBubbleAvatar />
      <ChatBubbleMessage>
        Message and other content here
      </ChatBubbleMessage>
    </ChatBubble>
  </ChatMessageList>
  <div className="flex-1" />
  <ChatInput
    placeholder="Type your message here..."
  />
  <Button
    size="sm" className="ml-auto gap-1.5">
    Send Message
    <CornerDownLeft className="size-3.5" />
  </Button>
</>
```

For more comprehensive examples, check out [this](https://github.com/jakobhoeg/shadcn-chat/blob/master/src/app/chatbot/page.tsx#L106-L175), [this](https://github.com/jakobhoeg/shadcn-chat/blob/master/src/app/chatbot2/page.tsx#L106-L175) & [this](https://github.com/jakobhoeg/shadcn-chat/blob/master/src/components/chat/chat-list.tsx#L54-L63) from the source code.

## Expandable Chat component

**v.0.2.0** adds additional functionality by adding an **expandable** chat component that you can use in conjunction with the other components to quickly build a chat-support type feature in your application.

`ChatSupport.tsx`:

```
import { ChatBubble, ChatBubbleAvatar, ChatBubbleMessage } from '@/components/ui/chat/chat-bubble'
import { ChatInput } from '@/components/ui/chat/chat-input'
import { ExpandableChat, ExpandableChatHeader, ExpandableChatBody, ExpandableChatFooter } from '@/components/ui/chat/expandable-chat'
import { ChatMessageList } from '@/components/ui/chat/chat-message-list'

export default function ChatSupport() {
  return (
    <ExpandableChat
      size='lg'
      position='bottom-right'>
      <ExpandableChatHeader className='flex-col text-center justify-center'>
        <h1 className='text-xl font-semibold'>Chat with our AI ✨</h1>
        <p>Ask any question for our AI to answer</p>
        <div className='flex gap-2 items-center pt-2'>
          <Button
            variant='secondary'
          >
            New Chat
          </Button>
          <Button
            variant='secondary'
          >
            See FAQ
          </Button>
        </div>
      </ExpandableChatHeader>
      <ExpandableChatBody>
        <ChatMessageList>
          <ChatBubble key={message.id} variant={message.sender === 'user' ? 'sent' : 'received'}>
            <ChatBubbleAvatar
              className='dark:invert'
              src={message.sender === 'user' ? '' : '/chatbot.svg'}
              fallback={message.sender === 'user' ? 'US' : 'AI'}
            />
            <ChatBubbleMessage variant={message.sender === 'user' ? 'sent' : 'received'}>
              {message.content}
            </ChatBubbleMessage>
          </ChatBubble>
        </ChatMessageList>
      </ExpandableChatBody>
      <ExpandableChatFooter>
        <ChatInput />
        <Button
          type="submit" size="icon">
          <Send className=size-4" />
        </Button>
      </ExpandableChatFooter>
    </ExpandableChat>
  )
```

And then use that component on all your sites by placing it in `layout.tsx` (Next.js)

`layout.tsx`:

```
 <html lang="en">
      <body>
        </main>
          {children}
          <ChatSupport />
        </main>
      </body>
```

Check out [this](https://github.com/jakobhoeg/shadcn-chat/blob/master/src/components/chat/chat-support.tsx#L61-L134) for a better overview of the api.