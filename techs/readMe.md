# Techniques Overview

In RouteOpt, we employ a range of sophisticated techniques to effectively tackle complex optimization problems. Below is
a summary of these key techniques:

1. **[Enumeration Tree Writing](./enumeration/readMe.md)**:
    - This approach involves addressing extremely challenging instances by meticulously constructing enumeration trees.
      It's a detailed method, especially effective for scenarios demanding high precision and exhaustive exploration of
      possible solutions.

2. **[Branching Strategies](./branching/readMe.md)**:
    - For insights into this technique, refer to the
      article [Two-Stage Learning to Branch in Branch-Price-and-Cut Algorithms for Solving Vehicle Routing Problems Exactly](https://www.researchgate.net/publication/374553305_Two-Stage_Learning_to_Branch_in_Branch-Price-and-Cut_Algorithms_for_Solving_Vehicle_Routing_Problems_Exactly).
      We compare the efficacy of 3PB with machine learning-based approaches. Notably, we have
      implemented the "best k" procedure within the machine learning-based method, enhancing its effectiveness in making
      branching decisions.

3. **[Hybrid Genetic Search (HGS)](./hgs/readMe.md)**:
    - For complex Capacitated Vehicle Routing Problems (CVRP), we integrate a heuristic method known as HGS. More
      information about this method can be found on
      the [HGS-CVRP GitHub repository](https://github.com/vidalt/HGS-CVRP). HGS is well-regarded for its efficiency and
      ability to generate high-quality solutions within a reasonable timeframe.

4. **[Dual Modification](./dual/readMe.md) (Coming Soon)**:
    - We are excited about the forthcoming introduction of the 'Dual Modification' technique. Although details are
      currently confidential, this method is anticipated to offer a novel approach to handling dual solutions in
      optimization problems. Updates on this innovative technique will be provided as they become available.

5. **[Deluxing](./deluxing/readMe.md) (Coming Soon)**:
    - 'Deluxing', another technique in development, aims to introduce advanced mechanisms for refining the enumeration
      process. We believe it will substantially improve both the efficiency and effectiveness of our optimization
      strategies.

Each of these techniques contributes significantly to RouteOpt's capability as a powerful tool for solving complex
optimization problems. We are dedicated to continually enhancing these techniques and introducing new advancements to
remain at the forefront of optimization technology.

As RouteOpt evolves, we encourage our users to stay informed about the latest developments and look forward to their
valuable feedback and contributions.
