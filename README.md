# CBOW
    if（cbow）{   //训练cbow架构
      // in  - > hidden
      cw = 0 ;
      for（a = b; a <window * 2 + 1 -  b; a ++）if（a！= window）{
        c = sentence_position  -  window + a;
        如果（c < 0）继续 ;
        if（c> = sentence_length）继续 ;
        last_word = sen [c];
        if（last_word ==  - 1）继续 ;
        for（c = 0 ; c <layer1_size; c ++）neu1 [c] + = syn0 [c + last_word * layer1_size];
        CW ++;
      }
      if（cw）{
        for（c = 0 ; c <layer1_size; c ++）neu1 [c] / = cw;
        if（hs）for（d = 0 ; d <vocab [word] .codelen ; d ++）{
          f = 0 ;
          l2 =词汇[word]。point [d] * layer1_size;
          //传播隐藏 - >输出
          for（c = 0 ; c <layer1_size; c ++）f + = neu1 [c] * syn1 [c + l2];
          if（f <= -MAX_EXP）继续 ;
          否则， 如果（f> = MAX_EXP）继续 ;
          else f = expTable [（int）（（f + MAX_EXP）*（EXP_TABLE_SIZE / MAX_EXP / 2））];
          // 'g'是梯度乘以学习率
          g =（1 - 词汇[word]。代码 [d]  -  f）* alpha;
          //传播错误输出 - >隐藏
          for（c = 0 ; c <layer1_size; c ++）neu1e [c] + = g * syn1 [c + l2];
          //学习隐藏权重 - >输出
          for（c = 0 ; c <layer1_size; c ++）syn1 [c + l2] + = g * neu1 [c];
        }
