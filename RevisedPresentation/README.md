# Exemplary Code Chunk
* This code chunk is the final slide of my presentation. I revised it to make it more readable.
* The graph is displaying the difference between the LDP vote percentage and the percent of welfare spending in the years 2015-2017 and 2020-2021.
* I chose this code chunk as it took me a considerable amount of time to create and make look good, much more so than any other graph.
* It was more complicated to create than I would've liked, but I think I made it look good and easily comprehensible in the end, so I am proud of it!

* I've included an image of the graph as a .png in this folder.

testplot <- ggplot(WelfareOnly, aes(x = wf2020, y = LDPvoteperc)) +
  geom_point() +
  geom_smooth(method = "lm", se = FALSE, color = "red") +
  labs(title = "Welfare (2020) vs LDP Vote % (2021)",
       x = "Welfare Value (2020)", 
       y = "LDP Vote Percentage (2021)") +
  theme_minimal()

finalplot <- ggplot(WelfareOnly) +
  geom_point(aes(
    x = wf2020, y = LDPvoteperc, color = "2020 Welfare vs 2021 Vote"),
    size = 2, alpha = 0.7, shape = 17) +
  geom_point(
    aes(x = wf2015, y = LDPvoteperc2017, color = "2015 Welfare vs 2017 Vote"),
    size = 2, alpha = 0.7, shape = 16) +
  geom_smooth(
    aes(x = wf2020, y = LDPvoteperc),
    method = "lm", se = FALSE, color = "red4", linewidth = 1.2) +
  geom_smooth(
    aes(x = wf2015, y = LDPvoteperc2017),
    method = "lm", se = FALSE, color = "blue4", linewidth = 1.2) +
  labs(
    title = "Welfare vs LDP Vote Share Over Time",
    subtitle = "Comparison of 2015-2017 and 2020-2021 Data",
    x = "Welfare Value", 
    y = "LDP Vote Percentage",
    color = "Time Period"
  ) +
  scale_color_manual(
    values = c(
      "2020 Welfare vs 2021 Vote" = "red4",
      "2015 Welfare vs 2017 Vote" = "blue4"
    )
  ) +
  theme_minimal(base_size = 20) +
  theme(
    plot.title = element_text(face = "bold", hjust = 0.5),
    plot.subtitle = element_text(hjust = 0.5, color = "gray"),
    axis.title = element_text(face = "bold"),
    legend.position = "bottom",
    legend.title = element_text(face = "bold"),
    panel.grid.minor = element_blank()
  )
finalplot
