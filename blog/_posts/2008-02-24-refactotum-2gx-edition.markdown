---
title: "Refactotum: 2GX edition"
layout: post
tags:
- grails
- groovy
- speaking
- testing
---
The inaugural [Groovy/Grails Experience (2GX)](http://jasonrudolph.com/blog/2007/12/20/2gx-next-gen-java-conference-is-right-around-the-corner/ "2GX - Next-Gen Java Conference Is Right Around the Corner") is in the bag, and as much as I was looking forward to it, it honestly *exceeded* my expectations rather significantly. The sheer enthusiasm for Groovy (and Grails) in the Java community is almost *palpable*.

![2GX T-Shirt](/resources/20080224-2gx-shirt.png)

The event capped off with a [new installment](http://www.groovygrails.com/gg/conference/speaker?speakerId=4738&amp;showId=131#pr8883 "Refactotum #6 - Grails") of [Relevance's Refactotum series](http://blog.thinkrelevance.com/twir "Relevance, Inc. - This Week in Refactoring").  Jay Zimmerman (Director of 2GX and the popular NFJS Symposium Series) was kind enough to dedicate the final afternoon of the conference to this unique session demonstrating the ease of contributing to open source, followed immediately by a workshop for putting those techniques into practice.  Coming out of the Refactotum, we had a widely diverse set of contributions, all of which make meaningful improvements to Grails.  The resulting set of patches involve [increasing test coverage](http://jira.codehaus.org/browse/GRAILS-2470 "[#GRAILS-2470] Patch: Additional Tests for WebUtils#getFormatFromURI - jira.codehaus.org"), [refactoring for readability](http://jira.codehaus.org/browse/GRAILS-2471 "[#GRAILS-2471] Patch: Increase Test Coverage and Improve Maintainability for GroovyIfTag class - jira.codehaus.org"), [boarding up broken windows](http://jira.codehaus.org/browse/GRAILS-2412 "[#GRAILS-2412] Patch: Resolve deprecation warnings in Grails build output - jira.codehaus.org"), [reducing complexity](http://jira.codehaus.org/browse/GRAILS-2471 "[#GRAILS-2471] Patch: Increase Test Coverage and Improve Maintainability for GroovyIfTag class - jira.codehaus.org"), and a handful of other improvements as well.  And perhaps the most rewarding part (for me, at least) of the three-day conference was talking to the several people that stopped by afterward, each to express that while they had never before understood just how easy it is to get involved in open source, now they know, and each seemed downright eager to contribute!

Special thanks to [Scott Davis](http://davisworld.org/ "Davisworld"), [Jeff Brown](http://javajeff.blogspot.com/ "Jeff's Mostly Java Web Log"), [Dierk König](http://www.manning.com/koenig/ "Manning: Groovy in Action"),  [Alex Tkachman](http://g2one.com/company.html#alex), [Alexandru Popescu](http://themindstorms.blogspot.com/ "mindstorm"), [Ken Kousen](http://kousenit.wordpress.com/ "Ken Kousen's Blog - Stuff I've learned recently"), and [Daniel Hinojosa](http://evolutionnext.com "evolutionnext.com") for their excellent and insightful contributions to the discussion!  

--

## Resources

### Slides

* [Refactotum #6 - Grails (2GX)](http://jasonrudolph.com/downloads/presentations/Refactotum_2GX.pdf)

### Helpful links and tools discussed

* [Jay Fields - Tests Reflect Code Quality](http://blog.jayfields.com/2008/02/tests-reflect-code-quality.html "Jay Fields Thoughts: Tests reflect code quality")
* [Code Coverage (Wikipedia)](http://en.wikipedia.org/wiki/code_coverage "Code coverage - Wikipedia, the free encyclopedia")
* [Grails Code Coverage Report](http://build.canoo.com/grails/artifacts/coverage/index.html "Grails Code Coverage Report")
* [Cobertura](http://cobertura.sourceforge.net)
* [easyb](http://www.easyb.org/ "easyb - Groovy BDD Framework")
* [Testing Private Methods in Ruby](http://jasonrudolph.com/blog/2007/11/02/evan-phoenix-on-testing-private-methods-in-ruby/ "Evan Phoenix on Testing Private Methods in Ruby")<sup>&sect;</sup>

### Resulting patches (Keep 'em coming!)

* [GRAILS-2412](http://jira.codehaus.org/browse/GRAILS-2412)
* [GRAILS-2469](http://jira.codehaus.org/browse/GRAILS-2469)
* [GRAILS-2470](http://jira.codehaus.org/browse/GRAILS-2470)
* [GRAILS-2471](http://jira.codehaus.org/browse/GRAILS-2471)
* [GRAILS-2521](http://jira.codehaus.org/browse/GRAILS-2521)
* [GRAILS-2527](http://jira.codehaus.org/browse/GRAILS-2527)       

<sup>&sect;</sup>The controversy of testing private methods isn't unique to Groovy...but seems common to Refactotums. ;-)
