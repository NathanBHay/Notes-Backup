A large part of design within the web, and by part applications, is the user experience, also called UX. UX is an important topic as it moderates the way in which end users interact with an application. There are many key principles which should be focused on when designing an interface. These pull from basic design ideas, to more complex psychology of design.

# Psychology of Design
Some of the most basic aspects of design come from psychology. This can be observed in the way applications should be made for people to be able to understand them innately. This can be done through the restriction of actions to force proper use, called affordances, as well as signifiers which can be signs or labels that inform the user. Another common form is mapping where previous behaviour from similar objects can be mapped onto the actions of a UI.

The most important psychological lesson is the idea that most people don't think at a subconscious level and as such most of the time use technology from an autopilot position. This means clarity should be focused on. With particular focus towards the ways UI can be used incorrectly.

# Minimalism
A large part of design is the focus on minimization. This process is most important during the early stages. Where a functional product with minimal features beats one that promises future features. Furthermore, the design of the first prototypes should avoid color, as it allows for focus on the size and positioning of objects.

# Design Hierarchy
A large part of UI design is the focus on the hierarchy of features that need to be included within the GUI.

# Refactoring UI Notes
These are rough notes on *Refactoring UI*:
- Start with a prototype that follows the current features directly. Don't over design by adding extra features that lack implementation.
- Leave details until later. This can be done by doing a rough sketch, and when in early prototyping stages holding the color. As most color draws attraction to the eye it can result in the positioning and scale of components to be thrown off. As such it is best to use grayscale early on. Don't focus too much on early design.
- Working in cycles means that instead of making one fully implemented component one should start with a simple design of each feature before more complex decisions are made. This is as it is easier to fix design problems later than attempting to start with edge cases. Also don't include features that haven't been added yet within the design. Be pessimistic and expect all features to be harder to implement than you believe.
- In general for fonts if you want an elegant or classic look serif typeface work the best. For more playful rounded sans serif, and for plainer looks neural sans serif.
- Basic color theory should always be used, but even without it just the presence of color draws attention to certain features.
- A small border radius functions for a neutral look, while a large border radius portrays a more playful look. No border radius feels more formal. Most of all stay consistent.
- An important part of UI is language. Less personal tones sound more professional, while casual language makes a site friendlier.
- Deciding what type of tone a website has is important to the application.
- Limit your own choices when designing is important. This can be done by assigning systems in advance, whether they be a list of similar shades of a color, or a restrictive font scaling.
- Some items you want to be systemized are - font size, font weight, line height, color, margin, padding, width, height, border radius, border width, opacity and box shadow.
- When picking colors or fonts start by guessing the result and then testing the adjacent options.
- A large part of design is visual hierarchy. This determines how important elements should appear in relation to one another. Doing this correctly will make any design look much better than superficial design choices such as shadow or edges. Visual hierarchy can be fixed by emphasizing important information and summaries, with color and scaling. While decreasing the size and scale of side information
- A common issue with hierarchy is over relying on font sizes. Commonly limiting the amount of font sizes can become very cluttered, so minimizes the difference between font sizes. This can be done by using font weights, or softer colors one some text.
- Don't use grey text on colored backgrounds. Instead find a new color based on the background color.
- An important paradigm is to emphasize by de-emphasizing.
- Avoid labels. Labels can be commonly removed if information is obvious, and correctly within the visual hierarchy. You can also avoid labels by adding clarifying text to form a sentence rather than a label.
- Labels should be treated as secondary. As most people associate the visual space with the data, you can de-emphasize labels.
- Labels should only be emphasized if people will be looking for the label, and the information is dense on the page.
- Use semantic HTML even if you have to restyle it.
- Balance weight and contrast. Use these two tools interchangeably if you want a good UI.
- When styling items on the hierarchy of important ensure primary actions are obvious with high contrast and colors. Secondary actions should be clear but not contrast. This can use an outline style or lowered contrast. Tertiary actions should be discoverable but unobtrusive.
- Destructive actions should only be big and red if its the primary action on the page.
- Starting with too much white space is the easiest way to clean up your UI. After this happens it should be removed and not added.
- Dashboards can have a more dense set of information.
- You don't have to fill the whole screen. Make sure to use margins.
- Use columns instead of making margins wider.
- Avoid percentage sizing if you don't want a component to shrink to small.
- Don't shrink a component until you need to.
- When shrinking elements for smaller screens shrink larger elements faster than small ones. Avoid relative units due to this.
- Avoid ambiguous spacing. This can be done with placing associated elements closer.
- Ignore typefaces with less than five weights. When using google fonts sort out styles with less than 10 weights.
- Optimize fonts for legibility. This means headlines should have tighter letters, spacing and shorter lowercase letters.
- Use popular fonts. People like consistency.
- A common strategy is to steal from people who care.
- Line length for paragraphs should maximize for best reading experience. This is when you should use EM units.
- If you are mixing paragraphs with images or components still limit line length.
- Align items by baseline for a cleaner look.
- Not every link needs a color. If links are used for titles just stick to a default color.
- Align with readability in mind. This means not centering long form text, but rather left aligned it once it gets over three lines.
- When aligning multiple columns make sure lines are all equal.
- Hyphenate justified text.
- Letter spacing should only be changed when tightening headlines or improving all caps legibility.
- Use HSL instead of RGB. HSL takes a position from the color wheel, and then sets the hue and saturation. When having lighter colors usually increase the saturation to avoid washed out colors.
- You can build a good color palette with - more than 5 greys, and more than 5 shades of your primary color. Commonly you need a secondary accent color, with around 5 shades, and then possibly a yellow, red, or green for state.
- Define a set of shades up front, avoid using darken and lighten shades. Your primary shade should be defined first.
- Darkest shade of your primary color should be text, while lightest shade should be background.
- When picking a shade start with the edges and middle, and then pick the in-between.
- You can find the perceived lightness of a color through $\frac{\sqrt{0.299r^2+0.587g^2+0.114b^2}}{255}$.
- A common way to change perceived brightness is through changing the intensity through the hue. The bright peaks of the hue spectrum are 60, 180, and 300. While the dark peaks are 0, 120 and 240.
- Greys can be cool or a warmer grey. This should go along with your .
- In general under the Web Content Accessibility Guidelines it is recommended that normal text has a contrast ration of 4.5:1, while larger has a 3:1. A common way to follow this is to flip contrast by using a light color on the background and dark color for the text inside.
- When it comes to colorblindness accessibility rely on color shades and symbols.
- Depth can be achieved by lighting all elements from above. This means drop shadow and inner shadow should be on the bottom and top respectively. The opposite is true if you want the object to feel its going into the page. The degree of this shadow and inset shadow should be controlled to make certain elements look deeper or stick out further than others. This can be used to highlight certain elements.
- To make elements feel more interactive you can change the shadow to make it look more pushed in.
- Commonly two shadows are used, one for the larger area, and one for the smaller darker area. This adds a perceived gradient to your shadow to simulate ambient and direct light.
- When using two shadows decrease the small dark shadow's size intensity as it raises.
- Depth can also be creased with color, with lighter representing closer elements while darker being for further away elements.
- Another way is to use vertically offset shadows with no blur.
- Overlapping elements creases an easy way to elevate elements more. This creates an appearance of layers.
- When working with images make sure they're good.
- When putting text over images ensure there is a higher contrast on the text. This can be done through a blur, applying a color, adding text shadow or darking the image.
- Don't shrink images.
- Control the shape and size of user generated content. This can be expanded by adding borders or shadow to force it to contrast correctly.
- Remember to always change basic elements such as dot points, punctuation marks, links, or any other element.
- Add color with accent borders.
- Change background colors as to make a more dynamic design.
- Use repeating patterns.
- When having empty states use more unique themes. A good example of this is google starts on a search page with only a title as opposed to a search window.
- Using less borders either through box shadow or background color differences can make a GUI look much cleaner.
- Think outside of the box. Instead of using the same techniques others use always think of a way to improve or increase clarity.
- A good way to improve is recreate interfaces.
