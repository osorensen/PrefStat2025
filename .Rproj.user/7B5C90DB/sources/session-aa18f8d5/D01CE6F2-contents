library(BayesMallows)
library(parallel)
cl <- makeCluster(7)
mod <- compute_mallows_mixtures(
  n_clusters = 1:7,
  data = setup_rank_data(rankings = sushi_rankings),
  compute_options = set_compute_options(include_wcd = TRUE),
  cl = cl
)
stopCluster(cl)

ggsave(
  filename = "figures/cluster_convergence.png",
  plot = assess_convergence(mod)
)

burnin(mod) <- 300

ggsave(
  filename = "figures/cluster_elbow.png",
  plot = plot_elbow(mod)
)
