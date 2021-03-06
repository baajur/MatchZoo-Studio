<template>
  <div id="mvlstm-description">
      <el-row :gutter="20">
        <el-col :span="15">
          <el-card>
            <el-scrollbar style="height:100%;">
              <div class="description-content">
                <h2>1. Introduction</h2>
                <p>The MV-LSTM model is a new deep architecture to match two sentences with multiple positional sentence representations. Specifically, each positional sentence representation is a sentence representation at this position, generated by a bidirectional long short term memory (Bi-LSTM). The matching score is finally produced by aggregating interactions between these different positional sentence representations which can aggregate different important contextualized local information in a sentence to support the matching , through k-Max pooling and a multi-layer perceptron.</p>
                <h2>2. Structure</h2>
                <p>The overall structure of the MV-LSTM is shown in the figure 1.  MV-LSTM consists of three parts: Firstly, each positional sentence representation is a sentence representation at one position which requires to reflect the representation of the whole sentence when attending to this position, so it is generated by a bidirectional long short term memory (Bi-LSTM); Secondly, the interactions between different positional sentence representations form a similarity matrix/tensor by different similarity functions----cosine, bilinear and tensor layer; Lastly, the final matching score is produced by aggregating such interactions through k-Max pooling and a multilayer perceptron.</p>
                <h2>3. Performances</h2>
                <p>The experiments of  MV-LSTM is conducted on  two task question answering and sentence completion with TREC QA dataset. The overall results are summarized in below Table.</p>
                <table class="result-data" cellspacing="0">
                  <caption>Table 1: Experimental results on QA.</caption>
                  <tr>
                    <th class="top-line">Model</th>
                    <th class="top-line">P@1</th>
                    <th class="top-line">MRR</th>
                  </tr>
                  <tr>
                    <td class="top-line">Random Guess</td>
                    <td class="top-line">0.200</td>
                    <td class="top-line">0.457</td>
                  </tr>
                  <tr>
                    <td>BM25</td>
                    <td>0.579</td>
                    <td>0.726</td>
                  </tr>
                  <tr>
                    <td class="top-line">ARC-I</td>
                    <td class="top-line">0.581</td>
                    <td class="top-line">0.756</td>
                  </tr>
                  <tr>
                    <td>CNTN</td>
                    <td>0.626</td>
                    <td>0.781</td>
                  </tr>
                  <tr>
                    <td>LSTM-RNN</td>
                    <td>0.690</td>
                    <td>0.822</td>
                  </tr>
                  <tr>
                    <td class="top-line">RAE</td>
                    <td class="top-line">0.398</td>
                    <td class="top-line">0.652</td>
                  </tr>
                  <tr>
                    <td>DeepMatch</td>
                    <td>0.452</td>
                    <td>0.678</td>
                  </tr>
                  <tr>
                    <td>ARC-II</td>
                    <td>0.591</td>
                    <td>0.765</td>
                  </tr>
                  <tr>
                    <td>MultiGranCNN</td>
                    <td>0.725</td>
                    <td>0.840</td>
                  </tr>
                  <tr>
                    <td class="top-line">MV-LSTM-Cosine</td>
                    <td class="top-line">0.739</td>
                    <td class="top-line">0.852</td>
                  </tr>
                  <tr>
                    <td>MV-LSTM-Bilinear</td>
                    <td>0.751</td>
                    <td>0.860</td>
                  </tr>
                  <tr>
                    <td class="bottom-line">MV-LSTM-Tensor</td>
                    <td class="bottom-line text-weight">0.766</td>
                    <td class="bottom-line text-weight">0.869</td>
                  </tr>
                </table>
                <br>
                <table class="result-data" cellspacing="0">
                  <caption>Table 2: Experimental results on SC.</caption>
                  <tr>
                    <th class="top-line">Model</th>
                    <th class="top-line">P@1</th>
                    <th class="top-line">MRR</th>
                  </tr>
                  <tr>
                    <td class="top-line">Random Guess</td>
                    <td class="top-line">0.200</td>
                    <td class="top-line">0.457</td>
                  </tr>
                  <tr>
                    <td>BM25</td>
                    <td>0.346</td>
                    <td>0.568</td>
                  </tr>
                  <tr>
                    <td class="top-line">ARC-I(Hu et al., 2014)</td>
                    <td class="top-line">0.475</td>
                    <td class="top-line">-</td>
                  </tr>
                  <tr>
                    <td>CNTN</td>
                    <td>0.525</td>
                    <td>0.722</td>
                  </tr>
                  <tr>
                    <td>LSTM-RNN</td>
                    <td>0.608</td>
                    <td>0.772</td>
                  </tr>
                  <tr>
                    <td class="top-line">RAE(Hu et al., 2014)</td>
                    <td class="top-line">0.258</td>
                    <td class="top-line">-</td>
                  </tr>
                  <tr>
                    <td>DeepMatch(Hu et al., 2014)</td>
                    <td>0.325</td>
                    <td>-</td>
                  </tr>
                  <tr>
                    <td>ARC-II(Hu et al., 2014)</td>
                    <td>0.496</td>
                    <td>-</td>
                  </tr>
                  <tr>
                    <td>MultiGranCNN</td>
                    <td>0.595</td>
                    <td>0.763</td>
                  </tr>
                  <tr>
                    <td class="top-line">MV-LSTM-Cosine</td>
                    <td class="top-line">0.665</td>
                    <td class="top-line">0.808</td>
                  </tr>
                  <tr>
                    <td>MV-LSTM-Bilinear</td>
                    <td>0.679</td>
                    <td>0.817</td>
                  </tr>
                  <tr>
                    <td class="bottom-line">MV-LSTM-Tensor</td>
                    <td class="bottom-line text-weight">0.691</td>
                    <td class="bottom-line text-weight">0.824</td>
                  </tr>
                </table>
                <h2>4. Reference</h2>
                <p>
                [1] Guo T, Lin T. Multi-variable LSTM neural network for autoregressive exogenous model[J]. arXiv preprint arXiv:1806.06384, 2018.
                </p>
                <p>
                [2] Guo T, Lin T, Lu Y. An interpretable LSTM neural network for autoregressive exogenous model[J]. workshop track on ICLR, 2018.
                </p>
              </div>
            </el-scrollbar>
          </el-card>
        </el-col>
        <el-col :span="9">
          <el-scrollbar style="height:100%;">
            <div class="description-content">
              <el-card>
                <el-scrollbar style="height:100%;">
                  <img src="../../../assets/mvlstm_structure.png" width="100%">
                </el-scrollbar>
              </el-card>
            </div>
          </el-scrollbar>
        </el-col>
      </el-row>
    </div>
</template>

<script>
  export default {
    name: 'Description',
    mounted: function () {
      // 为了得到卡片的高度，得到窗口的高度
      var winHeight = 0
      if (window.innerHeight) {
        winHeight = window.innerHeight
      } else if ((document.body) && (document.body.clientHeight)) {
        winHeight = document.body.clientHeight
      }
      if (document.documentElement && document.documentElement.clientHeight) {
        winHeight = document.documentElement.clientHeight
      }
      //设置两张卡片的高度
      document.querySelector('.el-card__body').style.height = winHeight - 60 - 20 - 40 - 10 - 70 + 'px'
      document.querySelectorAll('.el-card__body')[1].style.height = winHeight - 60 - 20 - 40 - 10 - 70 + 'px'
      // console.log(document.querySelectorAll('.el-scrollbar__wrap'))
      var scrollbar_list = document.querySelectorAll('.el-scrollbar__wrap')
      console.log(scrollbar_list)
      for (var i = 0; i < 4; i++) {
        scrollbar_list[i].style.overflowX = 'hidden'
      }
      //设置content区域的高度
      var content_block = document.querySelectorAll('.description-content')
      var content_height = winHeight - 60 + 'px'
      for (var i = 0; i < 2; i++) {
        content_block[i].style.height = content_height
      }
    }
  }
</script>

<style scoped>
  .description-content {
    text-align: left;
    font-size: 16px;
    line-height: 24px;
    font-weight: normal;
    font-family: "Lato", "proxima-nova", "Helvetica Neue", Arial, sans-serif;
  }

  .result-data {
    margin:auto;
    width: 60%;
    font-size: 15px;
  }

  .top-line {
    border-top: solid 1px black;
  }

  .bottom-line {
    border-bottom: solid 1px black;
  }

  .text-weight {
    font-weight: bold;
  }
</style>
