---
title: "EJB3 domain classes presentation at Grails eXchange: Slides, sample code, & rampant agnosticism"
layout: post
tags:
- grails
- speaking
---
As an extension to [last year's Grails + EJB3 tutorial on InfoQ.com](http://www.infoq.com/news/grails-ejb-tutorial "InfoQ Article: Grails + EJB Domain Models Step-by-Step"), I had the pleasure today of [presenting](http://www.grails-exchange.com/jason-rudolph "Grails eXchange 2007 : Jason Rudolph : EJB3 Entities and Grails") an updated demo on this topic, showing just how easy it is to pimp out your EJB3 entity beans to include all the slick dynamic goodness we've come to know and love from traditional Grails domain classes.  

 ![Groovy Duke - Pimp Extraordinaire](/resources/20071017-uncle-duke-logo.png)

But as much as I enjoy infusing boring, statically-typed EJB3 POJOs with GORM-powered productivity, I'm recently finding myself *more* excited about the ability to implement your Grails domain classes *with any technology you like*, and then simply expecting it all to just work.  The result?  Implementation-agnostic domain classes and the flexibility to use whichever technology is best suited for the task at hand.  We're free to choose...

## Traditional Grails domain classes

<pre lang="groovy">
class Castle {
    String name
    String country

    static belongsTo = [Knight]

    Knight knight
}
</pre>

## EJB3 entity beans (i.e., JPA-annotated POJOs)

(Some of the noise has been omitted here for sanity's sake.  Please feel free to [download the sample code](http://jasonrudolph.com/downloads/presentations/Grails_eXchange-EJB3_Entities_and_Grails-Example_Code.zip) for the full experience.)

<pre>
@Entity
@Table(name="knights")
public class Knight implements java.io.Serializable {

  private long id;
  private String name;
  private long numDragonsSlain;
  private Set<Sword> swords = new HashSet<Sword>(0);

  public Knight() {
  }

  // ...
  @Id
  @Column(name="knight_id", nullable=false)
  public long getId() {
      return this.id;
  }

  public void setId(long id) {
      this.id = id;
  }

  // ...

  @OneToMany(fetch=FetchType.LAZY, mappedBy="knight")
  public Set<Sword> getSwords() {
      return this.swords;
  }

  public void setSwords(Set<Sword> swords) {
      this.swords = swords;
  }          
}
</pre>

## JPA-annotated Groovy classes (i.e., POGOs)

<pre>
@Entity
@Table(name="sword_inventory")
public class Sword implements java.io.Serializable {

    @Id
    @Column(name="serial_number", nullable=false, length=12)
    String serialNumber

    @ManyToOne(fetch=FetchType.LAZY)
    @JoinColumn(name="assignee")
    Knight knight

    @Column(name="manufacturer", nullable=false)
    String manufacturer
}
</pre>

## Agnosticism runneth amuck

And regardless of the technology we choose for one domain class, we're *still* free to implement the other classes however we like.  The relationships remain intact, and GORM makes sure that it all just works.  Using the classes above, we can walk the relationships navigating from one implementation technology ... to another ... to yet another still.

<pre lang="text">
groovy> def c = Castle.get(1)
groovy> println "In the castle of ${c.name}, you can see ${c.knight.name} wield his mighty collection of ${c.knight.swords.size()} swords."
groovy> go
In the castle of Camelot, you can see King Arthur wield his mighty collection of 7 swords.
</pre>     

&nbsp;     
Cool!  Use the implementation most appropriate for your needs, and let the framework figure out the rest.

--

[Download the slides](http://jasonrudolph.com/downloads/presentations/Grails_eXchange-EJB3_Entities_and_Grails.pdf)

[Download the sample code](http://jasonrudolph.com/downloads/presentations/Grails_eXchange-EJB3_Entities_and_Grails-Example_Code.zip)
