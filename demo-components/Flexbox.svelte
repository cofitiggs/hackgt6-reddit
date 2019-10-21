<style>
  .flexy {
    display: flex;
  }
  /* 
    flex-direction: column = one on top of the other
    flex-direction: row = one next to the other
  */
  .row-basic {
    flex-direction: row;
  }
  .row-centered {
    flex-direction: row;
    justify-content: center; /*use justify-content to change alignment along MAIN axis (horizontal for flex-direction: row)*/
  }
  .row-spaced {
    flex-direction: row;
    justify-content: space-between;
  }
  .row-centered-vertical-horizontal {
    flex-direction: row;
    justify-content: center;
    align-items: center; /*use align-items to change alignment along CROSS axis (vertical for flex-direction: row)*/
  }
  .column-basic {
    flex-direction: column; /*use flex-direction to change direction of placement.*/
  }
  .column-centered {
    flex-direction: column;
    align-items: center;
  }
  .space-wide {
    flex: 1; /* use flex to say how much fractional space an element should take up. Apply this class to multiple elements and see what happens! */
  }
</style>

<section class="flexy column-centered">
  <img src="https://picsum.photos/200" alt="random image" />
  <p>Look ma, I'm a demo!</p>
  <a
    href="https://medium.com/free-code-camp/an-animated-guide-to-flexbox-d280cf6afc35">
    Learn more about flexbox here 👀
  </a>
</section>
